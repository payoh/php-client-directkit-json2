The LemonWay API (called Directkit) has two implementations: Directkit**Json2** and Directkit**Xml**. 

The Directkit**Json2** is recommended over the Directkit**Xml** because It is the simplest and the most network-efficient way.

To call the directkit**Json2** in PHP: use the [`curl_init`] to send a POST request (See also the [Postman example](http://documentation.lemonway.fr/api-en/files/4194929/image2017-1-30+11%3A8%3A29.png) in [our documentation](http://documentation.lemonway.fr/api-en/directkit/overview/requests-and-responses)).

This tutorial show how simple it is.

# Sample codes

```php
require_once "./Payoh.php";

try {
	$response = callService("GetWalletDetails", array(
	            "wallet" => "sc"
	        ));
	echo json_encode($response, JSON_PRETTY_PRINT);
}
catch (Exception $e) 
{
	echo ($e);
}
```
See also: [Payoh API documentation](https://payoh.me/documentazione) / method [`GetWalletDetails`](https://payoh.me/documentazione/api/directkit.wallets.get-details)

# How to run

After downloading this project (`git clone`), run:
```
php GetWalletDetails.php 
```
Out of the box it will call the `demo` environment. If you have your own test environment. You should fix the configuration in `LemonWay.php`, put your own environment configuration.

# Time to play!

The example is only the basic, you can also play with our API by calling other services. For example:
- [Create a new wallet](https://payoh.me/documentazione/api/directkit.wallets.register)
- [Create a payment link to credit a wallet](https://payoh.me/documentazione/api/directkit.moneyin.card.mi-web-initialize)
- [Credit the wallet without 3D secure](https://payoh.me/documentazione/api/directkit.moneyin.card.mi-credit-wallet)
- [Credit the wallet with 3D secure](https://payoh.me/documentazione/api/directkit.moneyin.card.mi-3d-initialize)
- [Create a payment form to credit a wallet](https://payoh.me/documentazione/api/directkit.moneyin.payment-form)
- [Register a Credit card to the wallet](https://payoh.me/documentazione/api/directkit.moneyin.card.mi-register-card)
- [Register an IBAN to the wallet](https://payoh.me/documentazione/api/directkit.moneyout.registeriban)
- [Transfer money from wallet to a bank account](https://payoh.me/documentazione/api/directkit.moneyout.moneyout)
- [Transfer money from wallet to other wallet](https://payoh.me/documentazione/api/directkit.p2p.sendpayment)

# Note

* The code only use PHP basic to stay framework-neutral. It only show you how easy to access to our service. In real project you might change it a litte, for example: wrap the `callService` in a service class in your Laravel project, or make a Symfony component for yourself.
* A good practices is to log any request / response (with Monolog for example) to our service in Development mode.


[`curl_init`]: http://php.net/manual/en/function.curl-init.php
[`SoapClient`]: http://php.net/manual/en/class.soapclient.php
[SoapClient]: https://github.com/payoh/php-client-directkit-xml-soap
[SoapClient SDK]: https://github.com/payoh/php-client-directkit-xml-soap-sdk
[LemonWay SDK]: https://github.com/payoh/php-client-directkit-xml
