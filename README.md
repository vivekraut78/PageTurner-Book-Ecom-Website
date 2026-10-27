# PageTurner - Online Bookstore (React)

A basic B2C e-commerce portal built with React and Vite for the TA-2 assessment, E-Commerce and ERP.

## How to run

1. Install Node.js (version 18 or newer) from https://nodejs.org
2. Open a terminal in this folder and run:

```
npm install
npm run dev
```

3. Open the address shown in the terminal (usually http://localhost:5173).

To create a production build, run `npm run build`.

## Demo accounts

- Admin: `admin@pageturner.com` / `admin123`
- Customer: use the Register option to create your own account
- Coupon code: `BOOK10` (10% off). Delivery is free for orders of Rs. 499 and above, otherwise Rs. 40.

## Folder structure

```
src/
  main.jsx                 entry point (Router + StoreProvider)
  App.jsx                  page layout and routes
  index.css                all styling
  context/StoreContext.jsx global state and business logic (cart, auth, orders, admin)
  hooks/useLocalStorage.js state that is saved in the browser
  data/books.js            starting book catalogue
  utils/format.js          price formatting helpers
  components/              Navbar, Footer, Toast, BookCover, BookCard, BookModal, AuthModal, OrderSummary
  pages/                   Home, CartPage, Checkout, OrderSuccess, Orders, Wishlist, Admin
```

## How it works (for viva)

- **Components and props**: each part of the page is a component. `BookCard` receives a `book` prop and shows one book.
- **State**: `useState` keeps temporary values such as the selected category or form fields.
- **Context API**: `StoreContext` shares the cart, wishlist, logged-in user, orders and books with every component, so no data has to be passed down manually.
- **Custom hook**: `useLocalStorage` saves the data in the browser, so the cart and orders remain after refresh. This acts as the database of the demo.
- **Routing**: React Router (`HashRouter`) switches between pages (`/`, `/cart`, `/checkout`, `/orders`, `/wishlist`, `/admin`) without reloading.
- **Business rules** (in `StoreContext`): subtotal, 10% coupon discount, delivery charge, order creation, cancellation and status updates.
- **Admin**: only the account with `admin: true` can open the dashboard, add or delete books and update order status.

## Limitations

Data is stored in the browser, payment is simulated, and passwords are stored as plain text. A real system would use a server, a database, password hashing and a payment gateway.
