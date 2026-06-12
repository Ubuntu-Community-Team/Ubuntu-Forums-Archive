---
title: "Unable to access folder"
date: 2013-02-14
forum: General Help
---

### Post by greytag on 2013-02-14
I am currently unable to acces contained folders in my /srv/webapps/ and I really can't fugure out why.

This is what **ls -lah** from within /srv/webapps/ looks like:
drwxrwxrwx  6 tomcat7 tomcat7 4.0K Feb 14 08:45 .
drwxr-xr-x  3 root    root    4.0K Feb 13 10:05 ..
drwxrwx--- 20 tomcat7 tomcat7 4.0K Feb 13 15:47 folder1
drwxrwx---  9 tomcat7 tomcat7 4.0K Feb 13 22:00 folder2
drwxrwx--- 10 tomcat7 tomcat7 4.0K Jun 21  2011 folder3
drwxrwx---  9 tomcat7 tomcat7 4.0K Feb 13 22:05 folder4

/etc/groups has this line:
tomcat7:x:115:adminstrator

I am logged in as administrator and have added this user to the tomcat7 group.

Thank you for your input.

// Jim

---

### Post by matt_symes on 2013-02-14
Hi
 
What is he output of 
 
```
 
groups

```
 
Did you log back out an in after adding administrator to the tomcact7 group ?
 
Kind regards

---

### Post by greytag on 2013-02-14
> **matt_symes said:**
> Hi
 
What is he output of 
 
```
 
groups

```
 
Did you log back out an in after adding administrator to the tomcact7 group ?
 
Kind regards

I did, twice.

THe output is: 
```
administrator adm cdrom sudo dip plugdev lpadmin sambashare
```

So I guess something isn't updated. Could it be a time thing, that I am logging out and then logging in too fast?

---

### Post by greytag on 2013-02-14
I see now that i misspelled 'administrator'. :oops:

Now it works, but I feel a little more stupid...

---

### Post by matt_symes on 2013-02-14
Hi
 
> **greytag said:**
> I see now that i misspelled 'administrator'. :oops:
 
I didn't notice that either #-o:D
 
Kind regards

---

