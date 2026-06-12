---
title: "double records in mysql table"
date: 2015-01-24
forum: General Help
---

### Post by johnnybgoode on 2015-01-24
how can i find double entries in a table?

---

### Post by SeijiSensei on 2015-01-25
Is there no unique field whatsoever?  Suppose, for instance, that every record has an email field.  Then you could run a query like:
```
select email,count(*) from table group by email order by count desc;
```
which will place any duplicated emails at the top of the list.  If it is possible that someone could have multiple legitimate records with the same email address, then you'll need to look at the entire record for the possible duplicates.

If you have control over the design of the database you need to start using primary keys.  Each record should have a unique identifier.

---

### Post by johnnybgoode on 2015-01-26
[SOLVED]
It works! Tank you SeijiSensei

---

### Post by btindie on 2015-01-26
> **SeijiSensei said:**
> Is there no unique field whatsoever?  Suppose, for instance, that every record has an email field.  Then you could run a query like:
```
select email,count(*) from table group by email order by count desc;
```


You can also use the 'HAVING' clause to further filter the records so it only shows those with duplicates, e.g.
```
SELECT COUNT(*), email FROM table GROUP BY email HAVING COUNT(*) > 1;
```

---

