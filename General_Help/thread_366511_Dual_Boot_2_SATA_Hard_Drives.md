---
title: "Dual Boot 2 SATA Hard Drives"
date: 2007-02-20
forum: General Help
---

### Post by richieblake on 2007-02-20
Hi all,

I've just started using ubuntu and while I have a little bit of an idea about using linux I'm having trouble setting up a dual boot with two hard drives.

Currently I have Windows XP installed on the first SATA drive.  I have Ubuntu installed on the second SATA drive.  Currently I am changing the boot sequence in BIOS to go between the two.  I find this to be quite annoying.  

I have tried reading other forum posts regarding this matter but am having trouble understanding some of the lingo.  Can anyone explain in more stupid terms how I might go about setting this up.

Cheers

---

### Post by markitect on 2007-02-28
The first thing you should do is look around for some reading on grub and the file menu.lst (located in /boot/grub)

Once you've gotten to know some about configuring grub you need to make sure you have grub installed.  
Set your bios to boot off the Linux drive.  and boot it up.  If it comes up to a menu with nice text menu, you are all set, go ahead and boot normally (it might also flash up at the top of the screen press esc to enter menu) which is also fine.  

Once your booted into Linux open up a terminal and type:
```
cat /proc/paritions
```
This will list all the paritions available on your computer and should have something like
```

/dev/hda
/dev/sda1
/dev/sdb1
/dev/sdb2
```
Thats assuming that sda1 is your windows drive and has one parition on it

now type gksudo edit /boot/grub/menu.lst If you search through the file it should already have a generic windows entry something like 
```

title Windows
rootnoverify (hd0,1)
makeactive
chainloader +1

```

Uncommenting this will add the option to boot to windows, but you will have to assign the proper place too boot from (hd0,1) will become something else most likely.  This is where your partitions come in.  grub numbers them 0 through whatever instead of a through whatever for the drive. also it numbers hd and sd drives together so number them as they are listed in partitions and they will probably be ok.   so in the above example if sda1 is the windows partition the corresponding entry in grub will probably be (hd1,0)  second drive, first partition.  you may have to play around to get it to work.

---

### Post by Azakus on 2007-02-28
Also, if your Windows partition is on the second drive and not the first, you have to add this after chainloader +1
```
map (hd1) (hd0)
map (hd0) (hd1) #Makes Windows think it is the first disk
```

---

