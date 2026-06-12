---
title: "Wireless problems with ubuntu 12.04 when installed per wubi in Windows 7"
date: 2014-11-05
forum: General Help
---

### Post by alopex38 on 2014-11-05
I installed ubuntu 12.04 via Wubi as a program in Windows 7 - it seemed quite straightforward - However when I called up ubuntu I first got a message  saying 'cannot read proc/mounts.

Then I rec'd an alarming message  when I tried to connect with my wireless router [zxel4965ton]  which stated 'system policy prevents modification of settings for all users - need authentication as a superuser - need password for root'.

I do not know how to proceed from here - I have no password for root.

Can anybody please help.

Many thanks

alopex38

---

### Post by hakuna_matata on 2014-11-05
> **alopex38 said:**
> I have no password for root.

It is the password which you use for your main user.

---

### Post by Impavidus on 2014-11-05
Indeed, you should be able to use sudo or your user password.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Also, note this:
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)
Wubi is not recommendable. Frankly, I think it always caused a lot of confusion.

---

### Post by bcbc on 2014-11-06
This is an old bug with 12.04 Wubi installs. If the wubi.exe you're using is out of date it downloads a bad diskimage (for 13.04) and installs that. Throw it away - you can't fix it.

Either install with the latest 12.04 wubi.exe if you're set on Wubi or do a  normal install as recommended. 

PS avoid 14.04 Wubi and 14.10 Wubi because they have other issues.

References:
[https://bugs.launchpad.net/wubi/+bug/1152708](https://bugs.launchpad.net/wubi/+bug/1152708)  Out of date Wubi 12.04 installs broken 13.04 disk image
[https://bugs.launchpad.net/wubi/+bug/1155704](https://bugs.launchpad.net/wubi/+bug/1155704)  13.04 installer doesn't create user account

---

### Post by alopex38 on 2014-11-06
Thanx to my three correspondents re Wubi - especially bcbc - will abandon Wubi and choose another route.

Kind regards

alopex38 in UK

---

