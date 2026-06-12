---
title: "Replace 10.10 grub with 12.04 grub"
date: 2013-01-22
forum: General Help
---

### Post by Bucky Ball on 2013-01-22
Hi all,

As the title suggests. I have 10.10 on one partition and 12.04 installed on another. The 10.10 is running the show at the moment and I want the 12.04 grub to replace it on sda as I am about to remove 10.10. Once I do that I'm figuring I won't be able to boot. At the moment, if there is a kernel update for 12.04 I need to boot to 10.10, sudo update-grub for the new kernel to show in the menu at boot.

How would I go about the switch? Tnx in advance. ;)

---

### Post by mikodo on 2013-01-22
This is from oldfred, the grub master.

Post # 2 (Fred's) states:

[I]"Which ever one you install last will be the default boot, but you can  easily change that by booting into which ever install you want as  default and run this":
[/I]
```
sudo grub-install /dev/sda
```[http://ubuntuforums.org/showthread.php?t=2075214](http://ubuntuforums.org/showthread.php?t=2075214)

If /dev/sda is the partition that the 12.04 install is on of course.

I sure you would have this on hand, as I do. Never had to use it though, so I can't comment on it:

[Boot Repair]("https://help.ubuntu.com/community/Boot-Repair")

Hope this helps.

;p

---

### Post by Bucky Ball on 2013-01-22
Thanks for that mikodo. Yes, oldfred is a grub guru, among other specialties. 

In my case, the one I installed first is the default boot. The 12.04 LTS grub is installed on the same partition as 12.04. 

I'll give that command a whizz and see what happens. Cheers. ;)

PS: Yes, Boot Repair is everybody's friend. Not sure if you're aware, but you can actually install  through Synaptics (or whatever you're using) and use it whilst running from the Ubuntu LiveCD desktop,  so the separate ISO is mostly not necessary. Amazing ...

---

### Post by Bucky Ball on 2013-01-22
Worked like a charm. Thanks. Solved. Something to pass along ...

---

### Post by mikodo on 2013-01-22
Again with oldfred's advice. Post # 2 again, shows how to check if you have changed the OS and partition to which grub 2 is attached to the MBR. You run the commands to check and repair, if you have to.

[http://ubuntuforums.org/showthread.php?t=2045764](http://ubuntuforums.org/showthread.php?t=2045764)

;p

---

### Post by Bucky Ball on 2013-01-22
Thanks but nutted all that out before doing anything with bootinfoscript and all is fine. Now time to install Grub Customizer and get it looking funky! Cheers.

PS: What I had previously was:

[QUOTE=oldfred]You can install to the same partition, just to in effect not install it. [/QUOTE] ... using 'Something Else' during 12.04 install. I wanted 10.10 to be running the show. Now it is well out of date and just sitting there - I haven't used it in quite some time except to update grub - I want it gone! I have three spare partitions then for playthings and will install their grubs to their partitions when it comes to that and my main squeeze, 12.04 LTS, will run the show until EOL. ;)

Thanks for the second link. Yes, oldfred's post is packed with info; again, very useful.

---

### Post by mikodo on 2013-01-22
Cheers!

---

