# SQL
practice with sqlite


# sqlite

1)How many users are there? 50 SELECT COUNT(*) FROM users;

2)What are the 5 most expensive items? SELECT * FROM items ORDER BY price ASC;
  Small Cotton Gloves
  Small Wooden Computer
  Awsome Granite Pants

3)What’s the cheapest book? (Does that change for “category is exactly ‘book’” versus “category contains ‘book’”?)

SELECT price, title FROM items WHERE category = "Books" ORDER BY price ASC;

SELECT price, title, category FROM items WHERE category LIKE '%Books%' ORDER BY price;

cheapest book is Ergonomic Granite Chair for both queries.

4)Who lives at “6439 Zetta Hills, Willmouth, WY”? Do they have another address?

SELECT user_id FROM addresses WHERE street = '6439 Zetta Hills' AND city = 'Willmouth' AND state = 'WY';

user_id = 40

SELECT * FROM addresses WHERE user_id = 40;

yes, there is a second address: 54369 Wolff Forges|Lake Bryon|CA|31587

5)Correct Virginie Mitchell’s address to “New York, NY, 10108”.

SELECT id FROM users WHERE first_name = 'Virginie' AND last_name = 'Mitchell';

UPDATE addresses SET city = 'New York', state = 'NY', zip = 10108 WHERE user_id = 39;

6)How much would it cost to buy one of each tool?

SELECT SUM(price) FROM items WHERE category = 'Tools';

$7383

7)How many total items did we sell?

SELECT SUM(quantity) FROM orders;

2125 items

8)How much was spent on books?

SELECT * FROM items WHERE category = 'Books'; - to get book id's

SELECT SUM(quantity) FROM orders WHERE item_id = 4; - for each book id

$661,990

9)Simulate buying an item by inserting a User for yourself and an Order for that User.

INSERT INTO users (id, first_name, last_name, email) VALUES (999, 'Travis', 'Montgomery', 'travisbm@gmail.com');

INSERT INTO orders (id, user_id, item_id, quantity, created_at) VALUES (777, 999, 4, 1000, '2015-09-08 00:40:31.307668');
