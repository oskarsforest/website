---
title:  "First SQL Project"
date:   2016-05-04 12:06:23
categories: [post]
tags: [SQL]
---

Wow! That's unexpected. While smoothies aren't making a lot of money for SpeedySpoon, they have a very high reorder rate. That means these smoothie customers are strong repeat customers.

Instead of recommending smoothies be taken off the menu, we should talk to the smoothie customers and see what they like so much about these smoothies. There could be an opportunity here to expand the product line, or get other customers as excited as these kale fanatics. Nice work!

Let's generalize what we've learned so far:

Data aggregation is the grouping of data in summary form.
Daily Count is the count of orders in a day.
Daily Revenue Count is the revenue on orders per day.
Product Sum is the total revenue of a product.
Subqueries can be used to perform complicated calculations and create filtered or aggregate tables on the fly.
Reorder Rate is the ratio of the total number of orders to the number of people making orders.

``` sql

select name, round(1.0 * count(distinct order_id) /
  count(distinct orders.delivered_to), 2) as reorder_rate
from order_items
  join orders on
    orders.id = order_items.order_id
group by 1
order by 2 desc;

```