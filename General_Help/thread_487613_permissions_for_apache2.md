---
title: "permissions for apache2"
date: 2007-06-29
forum: General Help
---

### Post by deepred on 2007-06-29
When I'm trying to load (in Firefox) a page from my localhost, I get a 403 error "You don't have permission to access / on this server." I tried chmod 777 /var/www, didn't work. Any ideas? Thanks

---

### Post by Andra on 2007-06-29
what address did you write in the browser address bar?
For example, I have a file phpinfo.php in my apache document root directory, so I request for
[http://ubsrv/phpinfo.php](http://ubsrv/phpinfo.php)

Apache document root directory I configured using webmin. Default was /var/www/apache2-default.

---

### Post by deepred on 2007-06-30
Hi Andra,
I typed [http://localhost/phpinfo.php](http://localhost/phpinfo.php) and it gave me a 403 error. It used to work though but then I tried to create a virtual directory which was located on a fat32 partition and it didn't work (same reason), I moved the files to /var/www/newdir and it didn't work either. This is when I started messing up with permissions and now I can't access my localhost with a browser, not even as root...

---

### Post by Megaqwerty on 2007-07-01
You need to run ```
sudo chown -R www-data:www-data /var/www
```
Then you should be able to access your site from a web browser

---

### Post by deepred on 2007-07-02
Still get the same 403 error after running sudo chown -R www-data:www-data /var/www. What's going with this thing? Should I maybe re-install apache?

---

### Post by Megaqwerty on 2007-07-02
Please give me the output of:
```
ls -l /var/ | grep www
```

---

### Post by deepred on 2007-07-07
Hi Megaqwerty, the output is:

```
drwxr--r--  5 www-data www-data  1024 2007-06-27 19:50 www
```

---

### Post by deepred on 2007-07-07
I've noticed that the chmod was set 744 so I changed to 755 and now the output is:

```
drwxr-xr-x  5 www-data www-data  1024 2007-06-27 19:50 www
```

Needless to say, it gives me the 403 error...

---

### Post by Megaqwerty on 2007-07-07
That's really odd...I don't know what could be causing it. I'd suggest purging apache at this point, and reinstalling (back up your config files if neccisary first) 
```
sudo aptitude purge apache2
```

-Megaqwerty

---

### Post by deepred on 2007-07-08
> **Megaqwerty said:**
> That's really odd...I don't know what could be causing it. I'd suggest purging apache at this point, and reinstalling

Yeah I did that and it fixed it, thanks for your help.

---

