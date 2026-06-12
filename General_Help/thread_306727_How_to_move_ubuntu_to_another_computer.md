---
title: "How to move ubuntu to another computer?"
date: 2006-11-25
forum: General Help
---

### Post by AdamTheCamper on 2006-11-25
My hdd is broken so I need to move my system to another pc.
Things I know to backup are **sources.list,xorg conf, /home directory **. 
Now I'd like to know how to get a **list **of all my installed **packages**, cause I don't want to spend a day folowing howtos to get everything back. So something I could copy to console and apt-get it. 

Anything else I've forgot?

Thx for sugestions.

---

### Post by qpieus on 2006-11-25
Try this:```
dpkg -l >installed_packages
```
This will make a file called installed_packages in your home directory.

This works too:```
dpkg --get-selections | sed -n 's/^\(.*\)\tinstall$/\1$/p' | cut -f1 > ~/installed_pkgs
```
There's also a way to use the generated list to have apt-get install all the items, but I don't have the link right now. If I find it I'll post here again.

---

### Post by konst88 on 2006-11-25
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by qpieus on 2006-11-25
Here's another link: [http://www.linuxforums.org/forum/debian-linux-help/40955-need-list-installed-packages.html]("http://www.linuxforums.org/forum/debian-linux-help/40955-need-list-installed-packages.html")
See post #3.
There's a typo in that post also. It's "dpkg -l ...." not "dpkg- l ...." in the second code box.

konst88's link shows a slicker way, IMO.

---

### Post by aysiu on 2006-11-25
If it's only the hard drive (hardware) and not the actual installation (software) that's broken, you should just copy over your Ubuntu partition using [PartImage](http://www.psychocats.net/ubuntu/partimage).

If you're more familiar with the command line, you can also do it with the *dd* or *tar* commands.

---

### Post by AdamTheCamper on 2006-11-25
thx, exactly what I need :D

---

### Post by MJN on 2006-11-25
The thing is, if your hard disk is broken how are you going to get the data off it? What do you mean by 'broken'?

Mathew

---

### Post by janjoker on 2007-12-21
> **aysiu said:**
> If it's only the hard drive (hardware) and not the actual installation (software) that's broken, you should just copy over your Ubuntu partition using [PartImage](http://www.psychocats.net/ubuntu/partimage).

If you're more familiar with the command line, you can also do it with the *dd* or *tar* commands.

So, this an also be a very simple way to move an exitsing installation to a new computer?
But what about drivers?

---

### Post by logos34 on 2007-12-21
> **janjoker said:**
> So, this an also be a very simple way to move an exitsing installation to a new computer?
But what about drivers?

Partimage (g4linux, clonezilla, etc) or dd command copy EVERYTHING as an IMAGE, an exact copy (hence the term clone)--even the partition(s) UUID stay the same.  You just have to reinstall grub to the destinattion drive's MBR.  But if you're moving to a new computer and not just new hdd, then differences in hardware may cause problems needing troubleshooting (graphics, network cards, audio, etc).

---

