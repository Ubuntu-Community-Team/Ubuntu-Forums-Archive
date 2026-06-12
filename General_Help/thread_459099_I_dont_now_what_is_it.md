---
title: "I dont now what is it?????????"
date: 2007-05-30
forum: General Help
---

### Post by pjalegria on 2007-05-30
Can someone help me please

I dont now what is "CD-ROM 1" and i cant delete it....:(

Tank you

---

### Post by taurus on 2007-05-30
How many CD/DVD drives do you have on your machine?

```
cat /etc/fstab
```

---

### Post by pjalegria on 2007-05-30
Just one...

---

### Post by reckless2k2 on 2007-05-30
please post the results of your fstab file. open a terminal window and type 

cat /etc/fstab

---

### Post by pjalegria on 2007-05-30
were it is

---

### Post by reckless2k2 on 2007-05-30
please do the same thing but this time type:

cat /etc/mtab

---

### Post by pjalegria on 2007-05-30
were it is the result

---

### Post by taurus on 2007-05-30
How about 

```
ls -la /media
```

---

### Post by pjalegria on 2007-05-30
were it is

---

### Post by pjalegria on 2007-05-30
I hope that someone can help me, please...

How do i fix that?

---

### Post by pjalegria on 2007-05-30
There are no solution for that??? should i do a reisntallation?

---

### Post by reckless2k2 on 2007-05-30
Well I'm not sure that you need to reinstall unless you really have nothing on there and it wouldn't matter. If you are not experiencing problems, you should be fine. Seems like a weird bug. I don't know if it's hardware or software related. If you pop a disc in, does it show up under CD-RW or CDROM?

If you are going to reinstall, backup your home directory so the reinstall will go smoother unless it's already in it's own partition. I can't remember if it is or not from the fstab.

I just checked and it's not. If you want to reinstall, just backup your home drive. It'll make a reinstall go smoother.

---

### Post by pjalegria on 2007-05-30
It did not want to make a reinstallation, i just want to fix that...I already i made 3 reinstalations after i leave XP, but i start to think there are too many bugs on Ubuntu....:(

when i pop a disc in, it show up under CD-RW

If someone can help me...

Tank you

---

### Post by pjalegria on 2007-05-30
I have made a reinstallation, everything ok, them after Kernel Update, same thing:(:(:(

---

### Post by reckless2k2 on 2007-05-31
this has something to do with the kernel update then. query a few things about the new kernel in this forum and it should answer. i noticed a few things popping up about the new kernel.

---

### Post by reckless2k2 on 2007-05-31
I read a few posts concerning the new kernel showing a phantom drive. I'm sure there will be a fix for it shortly. You can more or less ignore it until the patch is released which may be within the next day or so. This phantom drive will not "hurt" you or your system.

---

### Post by fanatik on 2007-05-31
are you using any usb memory sticks ? I have one, and when it is inserted there is a "phantom" cdrom appear. this is on a Sandisk Cruzer and is actually to do with there being a separate partition which helps it set up under Windows. I just ignore it.

---

### Post by cascader on 2007-06-09
This appears to be similar to the problem I am experiencing. See [post]("http://ubuntuforums.org/showthread.php?t=459763").

The phantom icon is on my Desktop and points to **[COLOR=Blue]/media/windows[/COLOR]** which is what I have called my **[COLOR=Blue]WinXP[/COLOR]** partition. I cannot delete the icon or rename it. [COLOR=Black]**Weird**[/COLOR]. Have checked **[COLOR=Red]fstab[/COLOR]** and **[COLOR=Red]mtab[/COLOR]**  as suggested - nothing. Will be keeping an eye on these posts but it seems no-one can come up with any answers. **[COLOR=SeaGreen]Cheers . . .[/COLOR]**

---

