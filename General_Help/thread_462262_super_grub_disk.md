---
title: "super grub disk"
date: 2007-06-02
forum: General Help
---

### Post by ReaLitaliano on 2007-06-02
i need help on fixing my boot 4 linux

---

### Post by confused57 on 2007-06-02
Here's information on how to use the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If you want to restore your Window's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You can use SGD or a Window's install cd(not a recovery cd) to do this.  Boot up with the Window's install cd, press "r" for recovery, then enter the command FIXMBR...this should get your Windows booting.

---

### Post by ReaLitaliano on 2007-06-02
thanks man but thats a lot to learn just to boot linux

---

### Post by louieb on 2007-06-02
> **ReaLitaliano said:**
> thanks man but thats a lot to learn just to boot linux
Setting up dual boot is just like installing a game in windows. right man.

---

### Post by ReaLitaliano on 2007-06-02
yea i know but something happen and now i cant boot to any OSs

---

### Post by adrian15 on 2007-06-03
> **ReaLitaliano said:**
> yea i know but something happen and now i cant boot to any OSs

The Herman webpage about Super Grub Disk is very big.

Just burn the SGD iso as you would burn another linux distribution.
Boot from it and select:

Linux -> Fix Boot of Linux

and you are done.

adrian15

---

### Post by ReaLitaliano on 2007-06-03
i tryed it before but i will try it again

---

### Post by adrian15 on 2007-06-03
> **ReaLitaliano said:**
> i tryed it before but i will try it again

Did you try exactly the same options I told you?

Did you see any error?

Were you using the last Super Grub Disk version?

adrian15

---

### Post by ReaLitaliano on 2007-06-03
ok i am using Super Grub Disk version 0.97 and the option i hit was gnu/linux then hit fix gnu/linux(grub) i then get a error 15 saying could not find file.

---

### Post by adrian15 on 2007-06-03
> **ReaLitaliano said:**
> ok i am using Super Grub Disk version 0.97 and the option i hit was gnu/linux then hit fix gnu/linux(grub) i then get a error 15 saying could not find file.

It seems that you will have to fix your filesystem with the fsck command from a live cd. I have no link for a howto on how to do it handy.


Why don't you try Linux -> Boot Linux meanwhile ?

adrian15

---

### Post by ReaLitaliano on 2007-06-03
where do i this in?

---

### Post by ReaLitaliano on 2007-06-03
do i use the linux boot cd

---

### Post by adrian15 on 2007-06-05
> **ReaLitaliano said:**
> do i use the linux boot cd

You should use something as Ubuntu desktop cd, not the alternate one.

Please ask someone else about more details.

adrian15

---

