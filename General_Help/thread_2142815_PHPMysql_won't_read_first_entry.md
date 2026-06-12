---
title: "PHP/Mysql won't read first entry"
date: 2013-05-06
forum: General Help
---

### Post by bandito40 on 2013-05-06
Hi,

I get the following error ```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/mysqlnd.so' - /usr/lib/php5/20090626+lfs/mysqlnd.so: cannot open shared object file: No such file or directory in Unknown on line 0

```
When I run the following script:
```
<?
$conn = new mysqli("localhost", "root", "password", "customers");

$rs = $conn->query("select name from customers limit 3;");
$row = $rs->fetch_object();
while($row = $rs->fetch_object()){
    echo $row->name."\n";
}

?>
```

It's spits out the error and then starts to list all entries expect for the first one. Also I am using Mysqli.

Surfed around but not luck as of yet.  Anyone have an idea what may be the problem?

---

### Post by bandito40 on 2013-05-07
I fixed my problem.  To correct the library not loading issue I renamed that file " /etc/php5/conf.d/10-mysqlnd.ini" to something else.  As for not reading the first entry in the table was a syntax error in my code.

---

