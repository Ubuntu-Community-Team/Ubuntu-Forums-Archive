---
title: "Can't rename files on Desktop... SCIM problem???"
date: 2007-11-19
forum: General Help
---

### Post by cisforcojo on 2007-11-19
Hey guys,

I just recently upgraded to Linux Mint 4.0 and this is the first time I'd ever had /home as a separate partition to keep all my stuff. Upgrading has been REALLY REALLY easy but I'm having a small problem and I -think- it didn't start until I tried to get SCIM working (for Chinese). Whenever I right-click on an icon in my Desktop, it will not let me rename it, it'll highlight the whole text (like before when I'd rename files) but I cannot type anything. This isn't a permission problem, I checked.

It's really bizarre. To double check, I just created a new file and could rename the file. So I tried renaming a desktop file again and no luck. Tried creating another new file and renaming it, also no luck. So it's really flaky. Any idea what this could be??????

Thanks!

---

### Post by cisforcojo on 2007-11-22
Bump!

---

### Post by purdticker on 2007-12-11
[https://bugs.launchpad.net/ubuntu/+source/scim/+bug/66104](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/66104)

> 2. If you do not use the deadkeys (often seen on European keyboards, and if you don't know what a deadkey is, you are not using it), you can change scim's "/FrontEnd/X11/Dynamic" setting. The procedure to change this setting is:
(a) Set scim not to start automatically (because it's useless to change the configuration file when scim is running) using the command "im-switch -s none". Log out and re-login.
(b) Edit your ~/.scim/config configuration file, change the /FrontEnd/X11/Dynamic option to true.
(c) Reset scim to start automatically with command "im-switch -s scim". Log out and re-login.

---

### Post by purdticker on 2007-12-11
I'm also using SCIM and chinese... I chose the second option.

Scim works fine &#21644;&#25105;&#33021;&#20889;&#27721;&#23376;&#12290;

---

### Post by slugicide on 2008-02-16
I have a similar problem, and I'm pretty sure it has to do with using SCIM for Japanese.  Which Is a must have for me.

---

