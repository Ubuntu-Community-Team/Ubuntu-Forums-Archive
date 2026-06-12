---
title: "pgadmin4 no such file or directory"
date: 2019-05-28
forum: General Help
---

### Post by datagueule on 2019-05-28
Hi All,

I m trying to launch pgadmin to work with SQL
I followed this for postgreSQL
[https://tecadmin.net/install-postgresql-server-on-ubuntu/](https://tecadmin.net/install-postgresql-server-on-ubuntu/)

then this for pgadmin4
[https://tecadmin.net/install-pgadmin4-on-ubuntu/](https://tecadmin.net/install-pgadmin4-on-ubuntu/)

unfortunately when I try to launch PgAdmin4 on my terminal by typing
```
http://209.121.xxx.82/pgadmin4 
```
 the terminal said "no such file or directory"

I found my IP by typing 

```
dig +short myip.opendns.com @resolver1.opendns.com
```


```

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic

```

Someone knows what is happening? 

thank you!

---

### Post by SeijiSensei on 2019-05-29
On a vanilla Ubuntu installation, to access that URL, the pgadmin4 application needs to be stored in /var/www/html/pgadmin4. Is that where it's located?

Have you tried [http://localhost/pgadmin4](http://localhost/pgadmin4)?

---

### Post by datagueule on 2019-05-30
```
datagueule@datagueule-ThinkPad-X220:/var/www/html$ ls
index.html

```

there is only index.html

I tried local host too 

```
datagueule@datagueule-ThinkPad-X220:~$ http://localhost/pgadmin4
bash: http://localhost/pgadmin4: No such file or directory

```

thanks for helping! do you have any other idea?

---

### Post by SeijiSensei on 2019-05-31
Did you install the pgadmin4-apache2 package as well as pgadmin4 as the article says?

[https://tecadmin.net/install-pgadmin4-on-ubuntu/](https://tecadmin.net/install-pgadmin4-on-ubuntu/)

If you did that, then maybe we can find the location of the pgadmin4 directory.  What do you see when you type "locate pgadmin4"? Any directory with an index.php or some other index file?  If you can find that, you could move it to the proper location with
```

cd /path/to/directory/above/pgadmin4
sudo mv pgadmin4 /var/www/html

```
Now give it a try.

---

### Post by datagueule on 2019-05-31
Hi!

with locate pgadmin4, I got a list super long, but at the end it was: 
```
/var/lib/dpkg/info/pgadmin4-apache2.conffiles
/var/lib/dpkg/info/pgadmin4-apache2.config
/var/lib/dpkg/info/pgadmin4-apache2.list
/var/lib/dpkg/info/pgadmin4-apache2.md5sums
/var/lib/dpkg/info/pgadmin4-apache2.postinst
/var/lib/dpkg/info/pgadmin4-apache2.postrm
/var/lib/dpkg/info/pgadmin4-apache2.templates
/var/lib/dpkg/info/pgadmin4-common.list
/var/lib/dpkg/info/pgadmin4-common.md5sums
/var/lib/dpkg/info/pgadmin4-common.postinst
/var/lib/dpkg/info/pgadmin4-common.prerm
/var/lib/dpkg/info/pgadmin4.list
/var/lib/dpkg/info/pgadmin4.md5sums
/var/log/pgadmin/pgadmin4.log
```

So I went on the  folder /var/log/pgadmin/ and typed:
```


sudo cp pgadmin4.log /var/www/html
```

But even with this:

```
datagueule@datagueule-ThinkPad-X220:/$ http://localhost/pgadmin4
bash: http://localhost/pgadmin4: No such file or directory


```

is it the right file to copy? 

thanks for helping!

---

### Post by datagueule on 2019-05-31
what is the terminal trying to do actually by typing 
[http://localhost/pgadmin4](http://localhost/pgadmin4)
?

---

### Post by SeijiSensei on 2019-06-01
Wait, you're typing "http://localhost/pgadmin4" at the teminal???  You have to open a browser and type that into the address bar.

---

### Post by datagueule on 2019-06-01
hahahahaha

I feel very stupid

its working

thanks haha

---

