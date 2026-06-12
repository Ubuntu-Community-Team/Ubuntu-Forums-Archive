---
title: "Xubuntu won't set as default boot in Linux dual-boot"
date: 2016-07-28
forum: General Help
---

### Post by JGreenidge on 2016-07-28
Greetings All!

Just to see whether I can improve performance on R31 Thinkpad installed with Xubuntu 16, I just installed Porteus 3.1 on the same only partition for dual booting. It works, all my Xubuntu files totally untouched, only thing now is the machine keeps only booting into Porteus whether I use F12 and F8 or not, no boot select or "grub" menu or anything. I wish to return to Xubuntu to stay yet keep Porteus as a crash recovery backup. I used Boot-Repair but Porteus still keeps loading on over Xubuntu. So can anyone recommend a Linux dual-boot menu maker?

Thanks!

Jim in NYC

---

### Post by QDR06VV9 on 2016-07-28
While it is booting spam the Shift key to see if Grub shows.
Most all Linux Debian based OS's use Grub Bootloader.
Also I remember this from their site:
> f you already have an OS installed on that drive and want to keep it  there, then you can run 'Porteus Installer' without clicking the option  to install a bootloader.  After the files are copied over, you'll just  need to point your existing bootloader to the Porteus data.

---

### Post by JGreenidge on 2016-07-28
Thanks for hyperswift replay! I both sat on the Shift key and machine-gun rapped it doing boot up but no change. Is there another way besides Boot-Repair to fix or replace the grub?

Thanks again!

Jim i NYC

---

### Post by QDR06VV9 on 2016-07-28
Have a look here: [http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/) 
[S]There is also an option to Choose which OS boots first[/S]...But Get Grub installed **Before** any other changes.
Boot-Repair is a Great Tool once you become familiar with it.:)

EDIT: Time got away from me I have to get ready and go to work now..will check back in the morning. 

And another method I have used with a Live CD installer: [URL="https://ubuntuforums.org/showthread.php?t=1581099"]https://ubuntuforums.org/showthread.php?t=1581099









[/URL]

---

### Post by yancek on 2016-07-28
In your initial post, you mention using boot repair but failed to post a link to the output so we have no useful information on your computer partitions, boot files or anything else related so, post the link.

---

### Post by oldos2er on 2016-07-30
Thread moved to General Help.

---

