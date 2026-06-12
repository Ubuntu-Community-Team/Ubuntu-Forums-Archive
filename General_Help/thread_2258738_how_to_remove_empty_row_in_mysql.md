---
title: "how to remove empty row in mysql"
date: 2014-12-30
forum: General Help
---

### Post by johnnybgoode on 2014-12-30
here's the snippet:

 Brooddeeg Figuren                         | Kristina Agate                  | hobby       |
|                                                    | NULL                              | NULL        |
| Alles in de wind                            | Ooos Blom                       | alg.        |
| Kriekenbolleke                             | Leen van Marcke                | alg.        |

---

### Post by schragge on 2014-12-30
```
DELETE FROM *table_name* WHERE *field2* IS NULL AND *field3* IS NULL
```

---

### Post by SeijiSensei on 2014-12-30
You can avoid this problem by using a primary key, and by specifying that required fields be "NOT NULL" when defining those fields' characteristics.  

See [http://dev.mysql.com/doc/refman/5.5/en/create-table.html](http://dev.mysql.com/doc/refman/5.5/en/create-table.html)

---

### Post by johnnybgoode on 2014-12-31
SOLVED   Thank you

---

