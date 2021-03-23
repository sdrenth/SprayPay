# SprayPay
SprayPay API client for PHP.

## Getting started
For usage and allowed parameters please view the official SprayPay API documentation. 

**Initialize client**
```
$client = new SprayPayApiClient();
$client->setApiKey('YOUR_API_KEY);
$client->setWebshopId('YOUR_WEBSHOP_ID');
$client->setTestMode();
```

**Run preflight request**
```
$response = $client->loanrequestpreflight->preflight([
    'emailAddress'       => 'some_email',
    'webshopOrderAmount' => '10.00',
    'webshopOrderId'     => 1,
    'webshopCustomerId'  => 1,
    'returnUrl'          => ''
]);
```

**Payment/Loan request**  

```
$loanrequest->create($data, true, true);
```

**Get order status**
```
$this->client->orderstatus->get(1);
```

**Create a chargeback request**
```
$client->chargebackrequest->create([
    'date'                      => '2020-02-02',
    'amount'                    => '10.00',
    'chargebackNotificationUrl' => '',
    'orderId'                   => 1,
    'reason'                    => 'Some reason'
]);
```

**Get chargeback request status**
```
$response = $client->chargebackrequest->getStatus(['reference' => 'SOME_REFERENCE']);
```

**Payment resource example**
```
$payment = new Payment($client->loanrequest->create($data, true, true));
$payment->isPaid();
```
