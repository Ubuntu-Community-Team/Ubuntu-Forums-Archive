---
title: "Root Login"
date: 2008-04-27
forum: General Help
---

### Post by dlovley on 2008-04-27
Hi,

So I did a fresh install of Heron after the fun of beta land and eveything worked perfectly :). I tried to setup my root account system/adm/user accounts/ etc. I unlocked and established a password for root user and checked all the permission boxes I could. Then I rebooted and attemted to log in as root. I get this message "The system administrator is not allowed to login from this screen". Couldn't find a clear answer in google or a forum search here. I understand that I wont need to use this often and that I do so at my own peril. I do however need the option. 

Darrel

---

### Post by dlovley on 2008-04-27
Oops,

Found the problem. System/admin/login window/security/allow administrator login. 

Darrel

---

### Post by chrisccoulson on 2008-04-27
You should never need to log in as root via GDM. It is disabled for very good reasons, as is the root account. Why do you need to do this?

---

### Post by dlovley on 2008-04-27
> **chrisccoulson said:**
> You should never need to log in as root via GDM. It is disabled for very good reasons, as is the root account. Why do you need to do this?

hehe,

Why does everybody get so fired up about this? Whats the worse that I could do? Blow up my computer and need to go through the hell of a 20 minute reinstall of my free ubuntu OS? Trust me I'm a big boy who can handle the access. :cool:

Darrel

---

### Post by fk4n on 2008-04-27
Because you will have the full access to all the files in a graphical user mode. It is easier than log in as normal user, but you could delete some important files by accident. Of course, if this computer isn't a important working PC, then you can do whatever you want. :)

---

### Post by chrisccoulson on 2008-04-27
As long as other (new) users reading this don't think that this is a good idea, then that's ok;)

---

### Post by dlovley on 2008-04-27
> **fk4n said:**
> Because you will have the full access to all the files in a graphical user mode. It is easier than log in as normal user, but you could delete some important files by accident. Of course, if this computer isn't a important working PC, then you can do whatever you want. :)

This particular machine is at home and I have two other windows Os's going on the HD and everything backed up off of the linux partion. So if I toast this system it's a matter of reinstall copy and paste. I am becoming a real fan of linux so I'm enjoying the learning process and all of the blunders that come with it. Would I set up a root login for my computer at work?... not a chance.

Darrel

---

### Post by kellemes on 2008-04-27
> **dlovley said:**
> hehe,

Why does everybody get so fired up about this? Whats the worse that I could do? Blow up my computer and need to go through the hell of a 20 minute reinstall of my free ubuntu OS? Trust me I'm a big boy who can handle the access. :cool:

Darrel

The worse that can happen is some cracker won't have a hard time getting into your system and steal whatever you have in it. If you really think about it, is this what you want?
Disabling your root account means a cracker will have to guess your user account, not an easy task.

Anyway, GNU/Linux should be about the freedom of choice, the day Ubuntu not only disables the root-account but also makes it impossible to enable it, I'll be the first to go somewhere else. ;-)

---

