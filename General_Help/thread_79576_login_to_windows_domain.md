---
title: "login to windows domain"
date: 2005-10-20
forum: General Help
---

### Post by jeanfrancoismelancon on 2005-10-20
Hi I'm a newbie on linux and I want to know if it is possbile to login directly to a windows domain (username, passw, and domain name) through the gdm greeter of ubuntu.

So it wont ask a password each time I want to access a ressource on my domain.

On some threads I herd of winbind but I can't get to install it on ubuntu 5.10

---

### Post by stevea1210 on 2005-10-21
[https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto?highlight=%28directory%29%7C%28active%29]("https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto?highlight=%28directory%29%7C%28active%29")


The above link is a great and simple how-to on adding Ubuntu pc's to an active directory domain.  I have used it on all of my ubuntu boxes, and can login using my AD accounts.  There is no domain field at the login so you login using DOMAIN(must be uppercase)+username.  After you complete the how-to, if you comment out the line ```
 winbind seperator = +
``` in your smb.conf, you can log in using DOMAIN\username.  It's my own personal prefernce.

Last night I actually wrote a script to do this process automatically.  I have a few more things to clean up on it, but once I get it ready, I'll post it in the forums.  The how to is easy, but a shell script is easier ;)

---

### Post by jeanfrancoismelancon on 2005-10-21
I'm stick at:

sudo net ads join

ads_join_realm: ads_add_machine_acct failed (ubuntu): Insufficent access

Any help here?

---

### Post by jeanfrancoismelancon on 2005-10-21
Ok, I got it

sudo net ads join -U username
:)

---

### Post by marvelchip on 2008-01-04
> **stevea1210 said:**
> [https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto?highlight=%28directory%29%7C%28active%29]("https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto?highlight=%28directory%29%7C%28active%29")


The above link is a great and simple how-to on adding Ubuntu pc's to an active directory domain.  I have used it on all of my ubuntu boxes, and can login using my AD accounts.  There is no domain field at the login so you login using DOMAIN(must be uppercase)+username.  After you complete the how-to, if you comment out the line ```
 winbind seperator = +
``` in your smb.conf, you can log in using DOMAIN\username.  It's my own personal prefernce.

Last night I actually wrote a script to do this process automatically.  I have a few more things to clean up on it, but once I get it ready, I'll post it in the forums.  The how to is easy, but a shell script is easier ;)


What do i add:
if i just type: /etc/default/ntpdate or /etc/krb5.conf  i get an error: command not found. Am i leaving out something?

---

### Post by jespdj on 2008-01-04
The file etc/default/ntpdate is in the package **ntpdate**; I looked it up on [http://packages.ubuntu.com](http://packages.ubuntu.com)

You can install it via Synaptic or by typing:
```
sudo apt-get install ntpdate
```

---

