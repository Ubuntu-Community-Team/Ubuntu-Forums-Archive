---
title: "How to set up ubuntu?"
date: 2008-02-24
forum: General Help
---

### Post by Jezz on 2008-02-24
Hello,

So yesterday my Vista crashed, couldnt even load it in safe mode(uxtheme.dll not found), tried to install windows xp but i dont have a floppy drive, and i need sata drivers for that. And its sunday so i cant go buy a floppy drive, so i need to work with linux until monday(or maybe thats a good thing lol).

Anyway,
So the only OS i can install now is Linux, i just installed Ubuntu 7.04. I am completely new to linux, and have a few questions,

I have a couple of issues now...
How do i install graphic drivers?(i have a nvidia geforce 8600gt)
Ubuntu 7.10 is the newest version, i have 7.04 now. Can i update or something?
How can i burn cd/dvds with ubuntu?

So far im impressed, especially since this OS is free, the only thing i need is graphic drivers :guitar:

---

### Post by shad0w_walker on 2008-02-24
If memory serves in 7.04 you can go to the restricted drivers manager to install graphics drivers. Should be in System > Administrations > Restricted drivers. It will give you a nice simple interface to install the driver.

As for upgrading, quite quite possible, though occasionally people have some issues. To be honest the odds are you don't need to upgrade but if you want to (And have the time/bandwith) then you can do so by hitting Alt-F2 and running this command:

```
gksu update-manager -c
```

That should open up the update manager and tell it to look for a newer release (7.10 at the moment) and allow you install the updates needed. Both this and the graphics drivers should come up with a prompt asking for your password, this is to make sure you are who you claim and to make sure you have the permissions to affect the whole system.

Burning CDs/DVDs is nice and easy too. If you have an ISO you want to write, stick a disc in the drive and right click the ISO, select 'Write to disc'. When you insert a blank CD/DVD you get prompted for an action, including a simple interface to burn files to the disc.

If you want a more advanced program I would suggest you have a look Add/Remove (Applications > Add/Remove) and search for K3B. It's fairly nero like and highly functional.

---

### Post by Jezz on 2008-02-24
Thanks. It says that i dont need a driver for my hardware, so that means all drivers are installed? Is there a way i can check this?

Burning isos is quite easy indeed :D
Well if i have time i will try to update.
And for a free OS, wow! Everything works out of the box, and a lot of apps pre installed. Lol maybe i dont even install windows again!:lolflag:

---

### Post by shad0w_walker on 2008-02-24
With the graphics drivers I'm not sure. If there is a tick box to give you the option of installing the drivers you might as well use it, if not I'm not sure why it's saying there are no needed drivers, the default install doesn't setup the official drivers by default.

---

### Post by steveneddy on 2008-02-24
If you only need Linux until Monday, why don't you just boot off of the Live CD and work from there.

I do that more often than not on systems that I know are not up to par but I need to get some work done.

The Live CD should give you most of the tools you need.

---

