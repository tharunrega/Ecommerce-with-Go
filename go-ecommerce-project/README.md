## Ecommerce with Go (Golang)

Minimal e-commerce API built with Go and Gin, using MongoDB for persistence.

### Quick Start

```bash
# Start local MongoDB and Mongo Express
docker-compose up -d

# Run the API (defaults to port 8000)
go run main.go
```

### Services

- **API**: `http://localhost:8000`
- **MongoDB**: `mongodb://development:testpassword@localhost:27017`
- **Mongo Express**: `http://localhost:8081` (username: `development`, password: `testpassword`)

Environment:

- **PORT**: optional, defaults to `8000`.

### Authentication & Users

- **Sign Up** `POST /users/signup`

  Request:

  ```json
  {
    "first_name": "Tharun",
    "last_name": "Rega",
    "email": "example@gmail.com",
    "password": "password",
    "phone": "+4534545435"
  }
  ```

  Response: "Successfully Signed Up!!"

- **Login** `POST /users/login`

  Request:

  ```json
  {
    "email": "example@gmail.com",
    "password": "password"
  }
  ```

### Products

- **Add Product (Admin)** `POST /admin/addproduct`

  ```json
  {
    "product_name": "Alienware x15",
    "price": 2500,
    "rating": 10,
    "image": "alienware.jpg"
  }
  ```

- **List Products** `GET /users/productview`

- **Search Products** `GET /users/search?name=<query>`

### Cart

- **Add to Cart** `GET /addtocart?id=<product_id>&userID=<user_id>`

- **Remove Item from Cart** `GET /removeitem?id=<product_id>&userID=<user_id>`

- **List Cart Items** `GET /listcart?id=<user_id>`

- **Checkout (Buy from Cart)** `GET /cartcheckout?id=<user_id>`

- **Instant Buy** `GET /instantbuy?userid=<user_id>&pid=<product_id>`

### Addresses

- The user can store at most two addresses: `home` and `work`.

- **Add Address** `POST /addaddress?id=<user_id>`

  ```json
  {
    "house_name": "white house",
    "street_name": "white street",
    "city_name": "washington",
    "pin_code": "332423432"
  }
  ```

- **Edit Home Address** `PUT /edithomeaddress?id=<user_id>`

- **Edit Work Address** `PUT /editworkaddress?id=<user_id>`

- **Delete Addresses** `GET /deleteaddresses?id=<user_id>`

### Notes

- Default API port is `8000` if `PORT` is not set.
- Ensure Docker is running before starting services.
- The repository imports reference `github.com/tharunrega/ecommerce-yt` in `main.go`.
