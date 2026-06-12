---
title: "postgresql foriegn key to read from another database's table"
date: 2017-10-30
forum: General Help
---

### Post by Sherman_Willden on 2017-10-30
If you know of a postgresql forum where I can post please let me know. So I have database sandbox01 and database sandbox02. In sandbox02 I have table test01 that looks like this: CREATE TABLE test01(my_last_name TEXT). What is the foreign key way for sandbox01 to recognize data from sandbox02's tables?

Thank you;

Sherman

---

### Post by SeijiSensei on 2017-10-30
Most of the time you reference a field in another table as tablename.fieldname.  There are so many different reasons to reference a foreign key that it's not possible to give a blanket answer.  Give us a specific example, like say a SELECT or something that involves a JOIN.

---

