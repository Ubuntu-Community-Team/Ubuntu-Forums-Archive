---
title: "Get Lastest Entries in Database"
date: 2008-01-22
forum: General Help
---

### Post by Black Mage on 2008-01-22
I'm working with a MS Access Database and I have information entered into a table using a auto number as the key. The interface I'm making with it is only suppose to get the last three entered events, or the highest auto_numbers. So my question is what is a sql command for getting the last three entries?

---

### Post by luisromangz on 2008-01-22
Try using SELECT TOP <number of rows> or BOTTOM, and an ORDER BY clause if necessary.

---

