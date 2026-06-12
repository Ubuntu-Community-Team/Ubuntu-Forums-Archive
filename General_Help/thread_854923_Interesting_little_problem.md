---
title: "Interesting little problem"
date: 2008-07-09
forum: General Help
---

### Post by eternalnewbee on 2008-07-09
****
Hi there.
Trying to clean up my second hard disk using GParted, when I noticed that I don't have swap on my main hard disk. Could that be why I can't start afresh with the second hard disk? (I hope I'm making some sense...).
See attachments for clarification.
PS I want a fresh start with /dev/sdb1/...****
I'm afraid if I somehow manage to format the second disk, my swap will be gone and I don't know if that would destabilize my system...
Also, I don't know how to resize my main hard disk; the only way I can think of, is by using an installation cd, but that would leave me in the middle of an installation...
what about using a live cd? Just thinking out loud, waiting for help...
___________________________________________________________________________________

There's no time like the present...

Ubuntu 8.04   Gnome 2.22.2   2.6.24-19-generic
AMD Athlon(tm) XP   899.219 MHz   256 KB
GeForce 7300 GT********

---

### Post by kidders on 2008-07-11
Hi there,

Depending on how much RAM you have (and how hard you push your machine), you may not need your swap space at all ... at least for a little while.

Personally, I would suggest replacing your swap partition with a swap file, at least on a temporary basis, while you reorganise your filesystems. Something like this ought to do the trick ...[LIST]
[*]Use **free**, **top**, etc. to get an idea for how much swap you need.
[*]Do something like **dd if=/dev/zero of=/var/swap bs=1M count=1024** to make a big file.
[*]Run mkswap on it to format it as swap space.
[*]**swapon** your new swap space.
[*]**swapoff** your old swap space.
[*]If you like, add an entry to your /etc/fstab to have the swap file activated automatically during boot.
[/LIST]

Swap files (ie like Windows and MacOS users have) don't tend to perform quite as well as swap *partitions* (which are preferred by most Linux users), but they're certainly more than adequate as a stop-gap measure.

Regarding resizing, any partition resizer that recognises the filesystems stored inside them will do fine, whether it's running off an install CD, a live CD, another Linux distro running on a different disk, etc. Just don't forget to make backups ... resize operations *can* screw up.

I hope that helps.

---

### Post by eternalnewbee on 2008-07-15
Thanks for your reply.
So I decided to install Linux TLE for my wife, because I had read somewhere that it offers the Thai fonts that everybody seems to use in Thailand. 
I inserted the cd and booted from it.
I configured the partitions manually and resized the hard disk. So now I had two Linux distros, or at least I thought I did. While in Linux TLE I can access my Hardy partition but when I try to boot Hardy it goes into a loop and eventually I get a message which says something like: intrafms... something
In other words: I can't get into my Hardy Heron!!!
Help****

---

### Post by eternalnewbee on 2008-07-15
...

---

