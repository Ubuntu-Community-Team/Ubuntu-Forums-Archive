---
title: "Can't access ENTIRE harddrive, computer possibly destroyed! :("
date: 2007-12-26
forum: General Help
---

### Post by Irishpolyglot on 2007-12-26
Hi guys, I've really dug myself in a deep hole and anyone that rescues me will be my personal hero for life!!!
I installed Ubuntu recently and was slowly getting into it and having fun. Meanwhile back in Windows I accidentally installed a driver update for an external harddrive that I really shouldn't have. When I booted up again, instead of getting the menu to select Ubuntu or Windows I went straight into an error message: "Grub Loading Stage 1.5. Grub loading, please wait....
Error 21."
No access to anything at all. So I put back in the CD I still had and reinstalled Ubuntu on a smaller partition (just 2GB). Now I can use the computer again, but sometimes at some boot-ups I get the message: "There was an error starting the GNOME Settings Daemon". All quite annoying, but I have a huge problem resulting from all of this:
I can ONLY access the 2GB 2nd Ubuntu installation!!! All of my important files on the Windows drive and on the 1st Ubuntu installation aren't there :(. If I go into places -> Computer, I just see the DVD drive and the Filesystem and *not* all the other drives that should be there...
PLEASE help me with this!! Keep in mind that I'm unfortunately a noobie with Linux so try to dum down anything if possible... Seriously I need your help guys :cry:
Thanks! You guys are the best!!!

---

### Post by Craigus on 2007-12-26
Try the supergrub disk :

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by Irishpolyglot on 2007-12-26
Thanks for the quick reply!! The program *seemed* to be the one that I was looking for; I went through all the options, but it could ONLY find the partitions of the 2nd Ubuntu installtion :( I went through several selections and always came to that conclusion of nothing else being available (only the Ubuntu installation and its swap drive were ever in the selections). When I uninstall the GNU GRUB, I just get a blank screen when I boot up. I tried all other options to gain access to Windows, but to no avail :((
And now I can't even boot back into the 2GB installation of Ubuntu!! I tried re-activating it, but all I get is the blank screen :(. I'll have to reinstall Ubuntu again just to access anything (am writing from other computer now).
Any other suggestions, or hints on using supergrub? It just doesn't see my other partitions. :(
Save me pleeeeeeease!!

---

### Post by meierfra on 2007-12-26
Boot from the ubuntu LiveCD and post the output of

```
sudo fdisk -l
```

---

### Post by Irishpolyglot on 2007-12-26
Am now running Ubunto from CD. Here is the output of that command:

> Disk /dev/sda: 160.0GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000
     Device Boot        Start            End         Blocks          Id   System
/dev/sda1   *                 1           370         2971993+   83   Linux
/dev/sda2                   371           491          971932+   82   Linux swap / Solaris

What does this mean? I don't like the looks of the 160GB not having my original files in it...

---

### Post by Craigus on 2007-12-26
meierfra's signature line has a link to Testdisk - that may be able to help.

---

### Post by meierfra on 2007-12-26
Click on testdisk in my signature. (Edit: You can install testdisk on the Ubuntu LIve CD via "sudo apt-get install testdisk")

---

### Post by Irishpolyglot on 2007-12-26
I just tried that but... "E: Couldn't find package testdisk" :( ... (it's just not my day), I'll investigate the link you gave for a download and read all of that information to hopefully get somewhere. cheers

---

### Post by meierfra on 2007-12-26
Probably you just need to enable  "universe" repositories:
Systems-> Administration->Software Sources"
Click on the Box next to "Community-maintained Open Source Software (universe)

---

### Post by Irishpolyglot on 2007-12-26
Thanks, that installed it for me. 
I ran testdisk (both the quick scan and the longer one) and it didn't find any FAT/Windows partitions :( :( :(

---

### Post by meierfra on 2007-12-26
> and it didn't find any FAT/Windows partitions

Bad news.  And testdisk is  my last line of defense. But maybe somebody else as some further suggestion.

---

### Post by meierfra on 2007-12-26
Did  try "photorec" (it gets  installed when you install  testdisk) ?

---

### Post by Irishpolyglot on 2007-12-27
I just tried that and it doesn't show any Windows files either (don't care so much about windows but my data stored in its folders). I don't get it; I literally installed a stupid driver program that must have altered the way the computer recognizes the disk, nothing was formatted!! Someone help me try to recover the data or the previous installation please...

---

### Post by Craigus on 2007-12-27
Some other free resources:

[http://www.thefreecountry.com/utilities/datarecovery.shtml]("http://www.thefreecountry.com/utilities/datarecovery.shtml")

You could try GetDataBack, but you would have to have the damaged disk in a windows machine. It is not free, but the free trial versions at least show you what can be recovered.

[http://www.runtime.org/downloads.htm]("http://www.runtime.org/downloads.htm")

---

