---
title: "salvage Ubuntu from W7 recovery"
date: 2013-07-02
forum: General Help
---

### Post by stephenbbb on 2013-07-02
I have a dual boot acer aspire and Ubuntu is fine. W7 got very sick and can't start and goes into a recovery console. 
it has two options: factory reset and save personal files. obviously the second one is my choice.

Q: what is the best way to proceed so as to save the Ubuntu partition (even grub maybe)?

I only use W7 to run tax software, but I really need to run that software.

---

### Post by Bucky Ball on 2013-07-02
*Thread moved to **Ubuntu, Linux and OS Chat**.*

***Reason: *** Not Ubuntu support request.

---

### Post by uRock on 2013-07-02
I'd back up the data in ubuntu. I was looking at my EeePC recovery disk and found where the script tells the partitioner to build a new partition table on the drive, which may destroy the ubuntu install. If it doesn't destroy the ubuntu install, then you may only have to install the grub boot loader, [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Mark Phelps on 2013-07-03
Looks like you're asking how to fix the Win7 problems but save off Ubuntu in the process, right?

To save off Ubuntu, I would download a burn a CD of Conezilla, boot from that (with an external drive connected) and use Clonezilla to image Ubuntu off to an external drive.  Using Clonezilla is a bit tricky because , unlike other image/restore apps, you have to enter the destination FIRST.

Do you have any kind of Win7 CD that came with the Acer? If so, then boot from that and look for an option to Repair Win7.  If you have that option, run it three times -- that's right, three times -- and see if that fixes the Win7 boot.

IF you don't have such a CD, then try using Boot-repair: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

If neither of these work, it's possible more got damaged in Win7 than the boot loader filesw.  If you have full install media (win7 DVD, not CD), you should then visit the Windows 7 forums (sevenforums.com) and read through their tutorial on how to do a repair install -- which will leave your apps, settings, and data intact.

---

### Post by Elfy on 2013-07-03
*Thread moved to **General Help**.*

---

### Post by stephenbbb on 2013-07-31
There is no CD or DVD, but all Acers have a hidden partition which is 20Gb. so it must have the full Win7 plus all the acer add-ons there. 
Since Win7 is as bad as Vista I am thinking of getting a pirate copy of WinXP and installing that over the Win partition. that will certainly wreck the MBR, but should not do anything to the Ubuntu partition. then there should be a way to fix the MBR and recover grub, so it allows me to load the Ubuntu partition and it will see WinXP.
If smb has done it before even better.

---

### Post by Bucky Ball on 2013-07-31
@stephenbbb: Your previous post has been deleted. Please be aware, from the forum's*** Code of Conduct***:

> Material that suggests illegal activity or contains illegal content is also forbidden. We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings. 

In this instance, a heads up only.

---

