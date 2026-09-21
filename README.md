## 3. التحليل والتصميم باستخدام مخططات UML

### أ. مخطط حالات الاستخدام (Use Case Diagram)
```mermaid
graph LR
    subgraph System["Cloud Bakery & Coffee Shop System"]
        UC1((Browse & Search Menu))
        UC2((Customize Coffee & Bakery))
        UC3((Place Order & Pay))
        UC4((Track Order Status))
        UC5((Manage Products & Inventory))
        UC6((Assign & Update Delivery))
    end

    Customer[Customer] --> UC1
    Customer --> UC2
    Customer --> UC3
    Customer --> UC4

    Driver[Delivery Driver] --> UC4
    Driver --> UC6

    Admin[Admin] --> UC3
    Admin --> UC5
    Admin --> UC6
```

---

### ب. مخطط الفئات (Class Diagram)
```mermaid
classDiagram
    class Product {
        +int productID
        +String name
        +double price
        +int stockQuantity
        +getDetails()
        +updateStock()
    }

    class Customer {
        +int customerID
        +String name
        +String email
        +String address
        +register()
        +placeOrder()
    }

    class Order {
        +int orderID
        +Date orderDate
        +double totalAmount
        +String status
        +createOrder()
        +cancelOrder()
    }

    class Payment {
        +int paymentID
        +String method
        +double amount
        +processPayment()
    }

    Customer "1" -- "0..*" Order : places
    Order "1" -- "1..*" Product : contains
    Order "1" -- "1" Payment : requires
```

---

### ج. مخطط المكونات والمعمارية (Component Architecture)
```mermaid
graph TD
    UI[User Interface Layer / App & Web] --> API[Application Logic Layer / Backend]
    API --> PaymentGateway[Payment Gateway API]
    API --> DB[(Database System / MySQL)]
```
