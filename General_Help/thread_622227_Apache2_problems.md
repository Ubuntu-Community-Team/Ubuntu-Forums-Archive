---
title: "Apache2 problems"
date: 2007-11-24
forum: General Help
---

### Post by lafferjm on 2007-11-24
I am having problems getting apache2 to work.  To install it i do 

```

sudo apt-get install apache2

```

After that i try 

```

sudo apache2ctl -k start

```

That step gives me an error.  It says that it can not open up httpd.conf because it does not exist to check this i do

```

whereis httpd.conf
```

and it turns out it truely isn't there.  How can i install apache2 and get it work.  It is confusing though because i have no problem getting apache1.3 to install and run.

---

### Post by IcemanV9 on 2007-11-24
It is fairly easy to install Apache2.

A good place to start from this [[COLOR="DarkOrange"]link[/COLOR]]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-42714b7a81f075c4f6024b8e0a36e2fccb11fdbd").

---

### Post by lafferjm on 2007-11-24
I installed it the way it said and that is when i got the error.  I did find xampp for linux though and got it set up.  Thanks for the help anyway :D

---

