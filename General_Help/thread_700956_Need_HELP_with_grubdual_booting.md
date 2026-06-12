---
title: "Need HELP with grub/dual booting"
date: 2008-02-18
forum: General Help
---

### Post by azwebti on 2008-02-18
Greetings all,

     I am still quite new to Linux and Ubuntu as I just successfully installed Ubuntu 7.10 Gutsy Gibbon about 2-3 weeks ago.  Having only 1 physical hard drive...I used Paragon Partition Manager to seperate and create a 20GB ext3 file partition from the free space on the NTFS partition.  This is what I've installed Gutsy onto.  I've managed to get everything customized and working just fine within Ubuntu.  I am loving my experience with Ubuntu and I would completely remove M$ from my life if I could get certain applications to be viable on Ubuntu.  Well until I've gotten the knowledge to do that I've decided to keep the installation of Windows XP Media Center Edition that came with my computer.

     This is where my problem starts.  When I try to boot into Windows by selecting it from the Grub boot menu.  Windows will bring up the screen saying that it did not shut down properly, and gives me the choice to boot into safe mode, last known good configuration, etc... No matter which option I choose, my computer will reboot.  The monitor goes blank and I can hear the hard drive heads moving around and stuff...then my computer will show its POST screen and show the grub boot menu again.
[I]
-----What I've done so far:[/I]
~I thought that since Windows was displaying its error screen that it was at least somewhat booting and the problem was within Windows itself. So I boot from the Windows cd and entered the recovery console.  In the recovery console I input "chkdsk /r" in hopes of repairing/replacing the defective Windows files.

~After two attempts of the above I Google'd "grub windows xp causes reboot" as well as many other keywords I thought would be related to my problem.  Many results lead to posts on Ubuntuforums.  But it seems that the results I found weren't exactly what I needed.  Nonetheless...I tried editing my /boot/grub/menu.lst file with some things I saw on the forums.

So after fighting with this problem for over a week I am running out of hope!  I was wondering if any of you Ubuntu veterans might be able to point me in the right direction.

Thank you much,
Adam Zwebti

[post edited for formatting and grammar]

---

### Post by azwebti on 2008-02-19
-bump-
Still having trouble with this...Please help someone.

---

### Post by strabes on 2008-02-19
It sounds like your windows installation is toast. This happened on my friend's laptop and we reinstalled windows (and GRUB - see the link in my sig for how to do that) and it worked fine.

---

### Post by phrawzty on 2008-02-19
I hate to break this to you, mate, but it sounds quite strongly like you have a toasted Windows partition.  I would strongly suggest mounting the partition from Linux, backing up any data you want to save, and re-installing.

Of course, be sure to keep a rescue CD of some type handy, as Windows will overwrite your MBR when it installs again, effectively removing your ability to boot to Ubuntu (via Grub).

---

### Post by azwebti on 2008-02-20
Thank you guys so much for the responses...

I agree with what the both of you said. But...I will back up my data and I am going to just format my whole darn HDD.  Just for the clean and fresh hard drive feeling.  Hope that I will be able to get things back up to speed quickly.  I think this time that I will make a partition fo r the Ubuntu OS, one for the Windows OS, and the bulk of it for data storage/program files.

---

