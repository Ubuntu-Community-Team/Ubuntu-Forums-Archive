---
title: "Cant open MySql prompt"
date: 2007-04-15
forum: General Help
---

### Post by proxima estacion on 2007-04-15
I installed Apache, MySQL now get an error message when trying to load the MySQL prompt. 
I type in" :~$ mysql"

and instead of getting the prompt I get "ERROR 1045 (28000): Access denied for user 'alindup'@'localhost' (using password: NO)"

I get the same message when trying to set the password using "mysql -u root"

any ideas or pointers??? thanks all!


EDIT: Resolved it with 'mysql -uroot -p'' mysql'

---

