---
title: "[SOLVED] Quick bash script syntax question"
date: 2008-07-08
forum: General Help
---

### Post by zyberwoof on 2008-07-08
I am trying to run a command in my script, but it doesn't seem to be working right.  If I run the command directly from the terminal, it works fine.  But from my script it does not.
```
$ mysql -u USERNAME -pPASSWORD -h 192.168.99.99 -e "SELECT * FROM TABLE" DBNAME
```

The above works just fine.  Now in my script...
```
#!/bin/bash

UIDPW="-u USERNAME -pPASSWORD -h 192.168.99.99 -e"
QUERY="\"SELECT * FROM TABLENAME\""

mysql ${UIDPW} ${QUERY} DBNAME
```

If I execute the script above, I get the same output as if I ran ```
$ mysql --help
```

I'm pretty sure that my problem is a scripting problem and isn't actually a problem with MySQL.  Any ideas on how to get my script syntax to work?

---

### Post by apswartz on 2008-07-08
try

```
QUERY='"SELECT * FROM TABLENAME"'
```

---

### Post by zyberwoof on 2008-07-08
Nope, that didn't do it.

I changed QUERY to QUERY='"DESCRIBE TABLENAME"' to make it as simple as possible, but it still doesn't work.

Thanks for the suggestion, though.

---

### Post by apswartz on 2008-07-09
Maybe you can break the variables up more.

```
#!/bin/bash

USERNAME=USERNAME
PASSWORD=PASSWORD
QUERY="\"SELECT * FROM TABLENAME\""

mysql -u ${USERNAME} -p${PASSWORD} -h 192.168.99.99 -e ${QUERY} DBNAME
```

P.S. I know next to NOTHING about mysql.

---

### Post by zyberwoof on 2008-07-09
> **apswartz said:**
> Maybe you can break the variables up more.

```
#!/bin/bash

USERNAME=USERNAME
PASSWORD=PASSWORD
QUERY="\"SELECT * FROM TABLENAME\""

mysql -u ${USERNAME} -p${PASSWORD} -h 192.168.99.99 -e ${QUERY} DBNAME
```

P.S. I know next to NOTHING about mysql.

Ha, that is exactly what I tried last night.  And yes, that does fix it.  I'm not sure why putting everything in one variable doesn't work, but when I did almost exactly what you suggested, it works.

My code looked like this...
```
mysql -u ${USER_NAME} -p${DB_PASS} -h ${DB_IP_ADDR} -e ${QUERY} DBNAME
```

I had a similar issue with another script earlier this year where I had to adjust my variable usage several times until it worked.  I guess BASH has some interesting quirks.

Thanks for your suggestions.

---

### Post by apswartz on 2008-07-09
Great!

---

