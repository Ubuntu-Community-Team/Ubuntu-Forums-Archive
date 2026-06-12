---
title: "[SOLVED] Can't change root password"
date: 2007-09-09
forum: General Help
---

### Post by berliita on 2007-09-09
My root password is the same as my user password (there's just a single user defined currently). I wish to change the root password, so it's different from the user password. I tried changing the root password via the dialog at System->Administration->Users and Groups, but this was ineffective.

Then i've read in some thread in this forum, namely 
[http://ubuntuforums.org/showthread.php?t=54726](http://ubuntuforums.org/showthread.php?t=54726), that in Ubuntu the root and all users are forced to share the same password. Is that so? If it is, 1) is this "feature" documented officially? 2) what's the rational that underlies it?

---

### Post by hashimoto on 2007-09-09
Facts here:
[https://help.ubuntu.com/7.04/administrative/C/](https://help.ubuntu.com/7.04/administrative/C/)

---

### Post by scxtt on 2007-09-09
as the 1st user created during install, it is given the ability to use sudo to gain root privs ... if you want to switch to root, you can do **sudo -s** and if you HAVE TO be able to login as root, do **sudo passwd root** ...

and no, users don't share a common password, that's just silly.

---

### Post by berliita on 2007-09-10
Thanks scxtt and, especially, hashimoto, for your replies. hashimoto, the document you linked to was exactly what i'd been looking for. Case closed.

---

### Post by bloozguy on 2007-10-11
> **scxtt said:**
> 
and no, users don't share a common password, that's just silly.

 Not so silly. I was shocked that everything is through sudo. If this is the same sudo that has been around for ages then to my mind that means there is a root password that I don't know and do not control. Sudo gives me "permission" to act as root but I am never root. I only get to use the root UID by way of sudo which is setuid.
If it is not set to the user password or something random somehow then YES everybody has a common password to begin with. Unless you change it IMMEDIATELY.

---

### Post by scxtt on 2007-10-13
> **bloozguy said:**
> Not so silly. I was shocked that everything is through sudo. If this is the same sudo that has been around for ages then to my mind that means there is a root password that I don't know and do not control. Sudo gives me "permission" to act as root but I am never root. I only get to use the root UID by way of sudo which is setuid.
If it is not set to the user password or something random somehow then YES everybody has a common password to begin with. Unless you change it IMMEDIATELY.what are you talking about?

---

