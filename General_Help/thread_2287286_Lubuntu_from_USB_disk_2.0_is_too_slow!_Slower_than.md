---
title: "Lubuntu from USB disk 2.0 is too slow! Slower than using usb in persistence mode."
date: 2015-07-18
forum: General Help
---

### Post by Ashesh_Shrestha on 2015-07-18
I installed lubuntu on my 32 gb pendrive but it freezes up very often. I believe it is due to disk activity(I read somewhere) and my pendrive also gets very hot. Running lubuntu with persistence was a bit more faster. How can I solve this problem? 


I read I can also use OS like puppy linux which runs entirely on ram. Can I also run lubuntu on ram like cache  datas which has higher I/O?

---

### Post by TheFu on 2015-07-18
Don't really know, but use faster media. USB2 is fine for emergency use and installs, but not much else.

If you need a really fast system, use TinyCore. [http://tinycorelinux.net/](http://tinycorelinux.net/) It makes puppy look like a dog. ;)

---

### Post by sudodus on 2015-07-18
Use the [boot option](https://help.ubuntu.com/community/BootOptions) ***toram***, and Ubuntu, Lubuntu, Xubuntu ..., will run on RAM.

[See also this link](http://ubuntuforums.org/showthread.php?t=2259682&p=13320397#post13320397) (and if you wish also the previous posts in the same tutorial thread)

*Edit:* This describes how to make a live system (or persistent live system) move the content of the squashfs to RAM, hence the name of the boot option, 'toram'.

---

### Post by v3.xx on 2015-07-18
How much ram do you have?

[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

It requires v14.04

---

### Post by sudodus on 2015-07-18
I described what to do with a persistent live system in post #2. v3.xx linked to terminator14's system in post #3, which is an advanced system. Both methods are worth trying :-)

---

