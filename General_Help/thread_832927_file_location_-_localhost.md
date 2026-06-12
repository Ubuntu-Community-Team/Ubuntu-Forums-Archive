---
title: "file location - localhost"
date: 2008-06-18
forum: General Help
---

### Post by gandalf458 on 2008-06-18
Hi - I've installed LAMP on my new laptop and can successfully navigate to localhost. I'm not all that clear about Ubuntu's filing system and would like to ask, where are my localhost files stored?

Thanks - G :)

---

### Post by justleen on 2008-06-18
/var/www/

---

### Post by gandalf458 on 2008-06-18
Great - thanks G :)

---

### Post by sisco311 on 2008-06-18
You can set the location in the */etc/apache2/httpd.conf* file:
> <VirtualHost *>
  ServerName *YourServerName*
  DocumentRoot */home/YourHomeFolder/www* 
</Virtualhost>*/var/www* is owned by root

*/home/YourHomeFolder/www *is owned by your user

---

### Post by StooJ on 2008-06-18
Quick hijack:

Are there security advantages in having the files stored in the user's home directory?

---

### Post by kesman on 2008-06-18
Not advantages, just that you don't need to be root to be able to put stuff in the shared directory.

---

### Post by gandalf458 on 2008-06-18
Thanks guys - and a helpful hijack, too! ;)

G :)

PS - I can't where to mark it as solved!!

---

### Post by gandalf458 on 2008-06-18
A further thought... If I change localhost to /home/user/www how do I then access PHPmyAdmin?

---

### Post by gandalf458 on 2008-06-18
> **sisco311 said:**
> You can set the location in the */etc/apache2/httpd.conf* file:

I've changed the http.conf file to point to /home/user/www and restarted Ubuntu (I haven't figured out how to stop and restart the http server yet) but localhost still seems to be looking in /var/www

Any idea what I might be doing wrong please?

---

### Post by gandalf458 on 2008-06-18
Oops! Just found my problem. Press F5!

---

### Post by kesman on 2008-06-19
> **gandalf458 said:**
> I've changed the http.conf file to point to /home/user/www and restarted Ubuntu (I haven't figured out how to stop and restart the http server yet) but localhost still seems to be looking in /var/www

Any idea what I might be doing wrong please?

You can restart apache with:
```

sudo /etc/init.d/apache restart

```
I guess. Hit TAB after typing init.d/ to see all the possibilities :P

---

### Post by snakdoc on 2008-06-19
thanks been looking for this

---

### Post by gandalf458 on 2008-06-19
> **kesman said:**
> You can restart apache with:
```

sudo /etc/init.d/apache restart

```
I guess. Hit TAB after typing init.d/ to see all the possibilities :P

Thanks. G :)

---

### Post by gandalf458 on 2008-06-19
I'm not sure what has happened between yesterday and today but I seem to be having trouble with my permissions although I have given create and delete permissions to everyone in my www directory.

When I navigate to a PHP page I get
```
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0
 
 Fatal error: Unknown: Failed opening required '/home/graham/www/php_vars.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
```

---

