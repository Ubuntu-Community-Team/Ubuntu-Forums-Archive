---
title: "[SOLVED] Can't write to HSF external hard drive"
date: 2007-12-19
forum: General Help
---

### Post by jmagick07 on 2007-12-19
I installed some stuff from Synaptic Package Manager, that was described as "write to HFS volume", but it didn't help...

I'm trying to copy files from Ubuntu to an external hard drive I formatted to work with my Mac computer.

Here's a screen shot of the error I get when I try to copy files to the external hard drive.

[IMG]http://i7.tinypic.com/6l1ouie.png[/IMG]

---

### Post by jmagick07 on 2007-12-19
anyone?  I have large files on this computer that I really need to put on the external drive.

---

### Post by jmagick07 on 2007-12-19
anyone?

---

### Post by jmagick07 on 2007-12-21
This sucks, I wanna backup some files on the external drive, but I can't....

---

### Post by t-bone510 on 2007-12-21
Yargh


```
sudo chmod 777 -R /media/PATHTOHDD
```

Do this while it is mounted.

---

### Post by jmagick07 on 2007-12-21
> **t-bone510 said:**
> Yargh


```
sudo chmod 777 -R /media/PATHTOHDD
```

Do this while it is mounted.

Wow that worked awesomely, thank!  It's currently copying files.

Question: Do I have to do this everytime I mount the drive, or is this a one-time thing I only had to do this one time - thus future mounts will "just work"?

---

### Post by t-bone510 on 2007-12-21
Nope. Will always have the permissions.

---

### Post by eeried on 2007-12-24
I have the same problem with an external HDD formatted to ext3. Same thing with a USB drive which I formatted to ext3.

When I first formatted it under Xubuntu-Feisty I never had to change the /media/disk permissions.

your workaround works fine of course, but that means you have to change permissions evrytime you plug your DD to a different computer running with Gutsy. 

BTW: @jmagick07 when you don't have permissions, you can always get them by switching to superuser:```
 sudo cp blahblah /media/pathtoyourdd
```

---

