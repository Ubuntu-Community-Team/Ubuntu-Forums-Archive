---
title: "PHP myAdmin Won't Log into Database"
date: 2016-09-02
forum: General Help
---

### Post by asker3 on 2016-09-02
Ubuntu 14.04

OK, I give up on this question.

I am working on installing a localhost server setup with php, phpmyadmin, and mysql.

It seems to have gone well until phpmyadmin. Phpmyadmin is not letting me log in. I don't have the right username and password and the defaults I can find don't work. I have tried to reconfigure it all including the database which won't complete. I have tried many things.

Thanks for any matches to shed a little light.

---

### Post by cariboo on 2016-09-02
Use the user name and password you created when you installed mysql.

---

### Post by asker3 on 2016-09-02
I don't remember what I put in.

---

### Post by asker3 on 2016-09-02
I have tried resetting the password with:
```
sudo /etc/init.d/mysql stop

sudo mysqld --skip-grant-tables &

mysql -u root mysql

Password=PASSWORD('YOURNEWPASSWORD') WHERE User='root'; FLUSH PRIVILEGES; exit;
```

I get the error: "#1045 Cannot log in to the MySQL server"

I removed ('YOURNEWPASSWORD') and replaced it with "PASSWORD 'not-telling' " (no double quotes just the single quotes and a space after PASSWORD. Is the syntax correct?

Thanks.

---

### Post by asker3 on 2016-09-03
Amazingly, I remembered the password. I would still like to know if my  syntax was correct and why I could not change the password from the  command line.

---

