---
title: "Cant restart/stop Apache 2 .. whats wrong?"
date: 2005-08-28
forum: General Help
---

### Post by nozey on 2005-08-28
I just instaled apache, php and mysql here.

I run apache:

```
$ sudo /etc/init.d/apache2 start
 * Starting web server (Apache2)...   [ ok ]
```

Everything works ok. I can access my website with php and mysql.
The problem begins when i try to stop the apache.

```
$ sudo /etc/init.d/apache2 stop
 * Stopping web server (Apache2)...   [fail]
```

I just cant stop him. Dont know why. The error.log:

```
$ tail -f /var/log/apache2/error.log
[Sun Aug 28 16:58:04 2005] [notice] Apache/2.0.53 (Ubuntu) 
PHP/4.3.10-10ubuntu4.1 configured -- resuming normal operations
```

I cant restart either:

```
$ sudo /etc/init.d/apache2 restart
 * Forcing reload of web server  (Apache2)...  [fail]

```

So ... the only way i found to stop apache was:
```

$ ps aux | grep apache
$ sudo kill -9 pid

or

$ sudo killall -9 apache2
```

But this is not a good way to stop apache. I can lose some datas.

Can anyone help me to fix this problem?

---

