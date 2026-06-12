---
title: "Triple OS install: can only boot Backbox"
date: 2015-09-10
forum: General Help
---

### Post by Nikhil_Shinde on 2015-09-10
Previously I was using xubuntu with windows 7 as a dual boot.It was working fine.But when I installed Backbox along with xubuntu and windows 7 as a triple boot.It was giving problem.It was showing only one operating system in boot menu that is backbox.So i am not able to load xubuntu or windows 7.Why this happened.Please help me to load my other operating systems.

---

### Post by VMC on 2015-09-10
I think [boot-repair]("http://ubuntuforums.org/showthread.php?t=1769482&p=10871917#post10871917") is what your looking for to fix your issue.

---

### Post by Bashing-om on 2015-09-10
Nikhil_Shinde; Hi ! Welcome to the forum.

In response to:
> 
So i am not able to load xubuntu or windows 7.Why this happened.Please help me to load my other operating systems.


There can be but one controlling boot authority. The last linux system installed is that authority. In your case blackbox.
You have to decide which operating system is to be in control of the boot process and install the boot code from that operating system ( Windows can not be that authority, as Windows will not play nice with any other operating system) .

Now linux will play with Windows and will chainload other operating systems onto it's boot menu. You just have to set the systems booting as per your desire for the primary booting system. Single hard drive ? Mult-hard drives with operating systems installed on individual physical hard drives ? As it makes a difference in installing the boot code.


[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-09-10
> **VMC said:**
> I think [boot-repair]("http://ubuntuforums.org/showthread.php?t=1769482&p=10871917#post10871917") is what your looking for to fix your issue.

Welcome. Try this, but first, open a terminal and:

```
sudo update-grub
```

Reboot. See all OSs? If not, boot-repair is your friend.

PS: I have changed the title of your thread to improve your chances of help. 'grub' is generic and gives no information about your support request. Good luck. :)

---

### Post by Nikhil_Shinde on 2015-09-11
[http://paste.ubuntu.com/12339931/](http://paste.ubuntu.com/12339931/)
When i tried boot-repair ,they give me above link.please help !!

---

### Post by Nikhil_Shinde on 2015-09-11
[http://paste.ubuntu.com/12339931/](http://paste.ubuntu.com/12339931/)
when i tried boot repair it gives me above link.Please help !!

---

### Post by oldfred on 2015-09-11
Do not know how BlackBox installs, but you used some choice that was erase entire hard drive and only install BlackBox.
You only show two partitions, swap & the Blackbox ext4 partition.

You may be able to use testdisk to restore some partitions, but whatever Blackbox overwrote is gone.

Best to just restore from you backups.

       [https://askubuntu.com/questions/286181/how-do-i-recover-my-accidentally-lost-windows-partitions-after-installing-ubuntu](https://askubuntu.com/questions/286181/how-do-i-recover-my-accidentally-lost-windows-partitions-after-installing-ubuntu)
Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Bashing-om on 2015-09-11
Nikhil_Shinde; Yuk !

I be the bearer of bad news . IF there is but the one hard drive (sda) on this system you are in for a real hard time to recover files.
On sda there is but blackbox installed. No other operating system exists.

If on this hard drive you DID have other operating systems installed, you "might" be able to recover files.
see:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[INDENT][INDENT]sad
[INDENT][INDENT][INDENT]and the truth can hurt
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-09-11
Snap!

---

### Post by ventrical on 2015-09-11
There is a super slim chance the grub_rescue might be able to find missing. So .. to the OP .. you have to look up Grub_rescue, download the image and burn it to CD.

Regards..

---

