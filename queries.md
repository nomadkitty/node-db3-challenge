# Database Queries

### Display the ProductName and CategoryName for all products in the database. Shows 76 records.

```sql
SELECT p.productName as Product
, c.categoryName as Category
FROM [Products] as p
join Categories as c on p.categoryId = c.categoryId
```

### Display the OrderID and ShipperName for all orders placed before January 9, 1997. Shows 161 records.

```sql
SELECT o.orderID
, o.orderDate
, s.shipperName
from orders as o
join shippers as s on o.shipperId = s.shipperID
where o.orderDate < '1997-01-09'
```

### Display all ProductNames and Quantities placed on order 10251. Sort by ProductName. Shows 3 records.

```sql
SELECT o.orderId
,p.productName
, o.quantity
FROM [OrderDetails] as o
join products as p on o.productId = p.productId
where o.orderId = 10251
order by p.productName
```

### Display the OrderID, CustomerName and the employee's LastName for every order. All columns should be labeled clearly. Displays 196 records.

```sql
SELECT o.orderId
, c.customerName as Customer
, e.lastname as EmployeeLastName
from orders as o
join customers as c on o.customerId = c.customerId
join employees as e on o.employeeId = e.employeeId
```

### (Stretch) Displays CategoryName and a new column called Count that shows how many products are in each category. Shows 9 records.

```sql
SELECT c.categoryName
, count(*) as count
FROM [Products] as p
join categories as c on p.categoryId = c.categoryId
group by p.categoryId
```

### (Stretch) Display OrderID and a column called ItemCount that shows the total number of products placed on the order. Shows 196 records.

```sql
SELECT orderID
, sum(quantity) as ItemCount
FROM [OrderDetails]
group by orderId
```
