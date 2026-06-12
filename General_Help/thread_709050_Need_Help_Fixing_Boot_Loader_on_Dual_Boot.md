---
title: "Need Help Fixing Boot Loader on Dual Boot"
date: 2008-02-27
forum: General Help
---

### Post by zigx on 2008-02-27
Hi Guys,

I have a weird situation.  I have a dual boot system windows and ubuntu.

Everything was fine until i reinstalled XP on the windows partition and the Grub boot loader (installed by default by ubuntu) was apparently overwritten.

My question is how do i reinstall grub without risking damage to my Windows data?  

I absolutely can NOT lose any data.... is there a safe route i can take to restore grub as the boot loader and properly recognize my windows and linux setups?

thank you!

---

### Post by housam on 2008-02-27
Use [[COLOR="Red"]_this guide _[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")to recover Grub

---

### Post by geo909 on 2008-02-27
> **housam said:**
> Use [[COLOR="Red"]_this guide _[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")to recover Grub

+1 to that. Just wanted to mention you should go to the "Overwriting the Windows boot loader" section. In his example, he uses "hda" for his disk and "hda1","hda2" etc for his partitions. You may have to use "sdx" (x=a,b,c...) if you have a SATA disk. So, your first partition in your first hard disk would be "sda1". The only tricky part is to find out in which disk/partition your filesystem lies.

Well, sorry if I mention things you are already familiar with.

By the way, there is a thing called "Super Grub Disk" which claims to restore GRUB automagically (including also manual or other ways). If you don't succeed with the guide, maybe it worths to give it a try.. 

[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

---

### Post by zigx on 2008-02-28
incredible.  the ubuntu docs have EVERYTHING covered...so much covered id ont even know where to begin looking lol.

thank you guys so much for your input... will givethis a shot over the weekend.

---

