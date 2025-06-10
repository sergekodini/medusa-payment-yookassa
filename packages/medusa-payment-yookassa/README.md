<p align="center">
  <a href="https://www.medusajs.com">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://github.com/user-attachments/assets/9a99f9e8-f80e-4411-9bed-6e2032b1ab1c">
      <source media="(prefers-color-scheme: light)" srcset="https://github.com/user-attachments/assets/9a99f9e8-f80e-4411-9bed-6e2032b1ab1c">
      <img alt="Medusa logo" src="https://github.com/user-attachments/assets/9a99f9e8-f80e-4411-9bed-6e2032b1ab1c" height="120">
    </picture>
  </a>
  
</p>

<h1 align="center">
YooKassa Payments for Medusa
</h1>

<p align="center">
A Medusa plugin that provides YooKassa payments.
</p>

<p align="center">
  <a href="https://t.me/medusajs_com">
    <img src="https://img.shields.io/badge/Telegram-Join_Medusa_Community_Chat-0088cc?logo=telegram&style=social" alt="Join on Telegram" />
  </a>
</p>

<p align="center">
  <a href="https://medusajs.com">
    <img src="https://img.shields.io/badge/Medusa-^2.7.0-blue?logo=medusa" alt="Medusa" />
  </a>
  <a href="https://medusajs.com">
    <img src="https://img.shields.io/badge/Tested_with_Medusa-v2.8.4-green?logo=checkmarx" alt="Medusa" />
  </a>
</p>

## Prerequisites

- Medusa server v2.7.0 or later
- Node.js v20 or later
- A [YooKassa](https://yookassa.ru/joinups/?source=ks) account, a shop identifier `shopId` and a secret API key `secretKey`.

## Installation

```bash
yarn add medusa-payment-yookassa
# or
npm install medusa-payment-yookassa
```

## Configuration

Add the provider configuration in your `medusa-config.js` file of the Medusa admin application:

```js
# ...
module.exports = defineConfig({
  # ...
  modules: [
    {
      resolve: "@medusajs/medusa/payment",
      options: {
        providers: [
          {
            resolve: "medusa-payment-yookassa/providers/payment-yookassa",
            id: "yookassa",
            options: {
              shopId: process.env.YOOKASSA_SHOP_ID,
              secretKey: process.env.YOOKASSA_SECRET_KEY,
              capture: true,
              paymentDescription: "Test payment"
            },
          }
        ]
      }
    }
  ]
})
```

Add environment variables:

```
YOOKASSA_SHOP_ID=1234567
YOOKASSA_SECRET_KEY=live_secret_api_key
```

Then, set up a webhook URL for notifications from YooKassa [here](https://yookassa.ru/my/merchant/integration/http-notifications). The URL should be in the following format:

```
https://{YOUR_MEDUSA_DOMAIN}/hooks/payment/yookassa_yookassa
```

## Storefront Integration

Make the necessary changes to your Medusa storefront.
You can refer to the modifications made in the [Medusa Next.js Starter Template](https://github.com/medusajs/nextjs-starter-medusa), which are located in the [`examples/medusa-storefront`](https://github.com/sergkudinov/medusa-payment-yookassa/tree/main/examples/medusa-storefront) directory.
To see the exact differences, check the [comparison page](https://github.com/sergkudinov/medusa-payment-yookassa/compare/v0.0.0...main).

## Development

Find documentation on bootstrapping a development environment [here](https://github.com/sergkudinov/medusa-payment-yookassa/tree/main/examples).

## 💬 Support & Community on Telegram

Join the [Medusa Telegram community chat](https://t.me/medusajs_com) to discuss features, get support, and connect with developers building on Medusa.

## License

Licensed under the [MIT License](LICENSE).