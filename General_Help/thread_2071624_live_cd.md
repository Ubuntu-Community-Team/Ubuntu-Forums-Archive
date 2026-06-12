---
title: "live cd"
date: 2012-10-15
forum: General Help
---

### Post by unibroker on 2012-10-15
I am currently dual boot Precise and WinXP.  I was told I need to do a clean install of Precise because I'm going from 32 to 64 bit.  I burned the iso and I saw a discussion on these forums where there is a procedure to do a clean install without disturbing the XP portion.

I boot the iso and get to the screen where you choose between Try Ubuntu and Install Ubuntu.  When you choose Install Ubuntu is the next screen where you choose where you want to install it?  The poster talks about a Something Else choice which is where I want to go.  Right now I have some gparted maintenance I need to do before I do this install.  Just trying to get my ducks in a row.

Thanks in advance.

---

### Post by Bashing-om on 2012-10-16
ducks in a row is a very good thing.
as you have xp installed I am going to assume booting via bios, thereby no fretting over GPT partitioning or UEFI booting.
install screen :  12.04 version is the second screen the best I recall, 1st being software download details, the install is the 3rd option on that screen and maybe listed as manual partitioning (?)


Yeah, setting up dual booting is a fairly straight forward process with these warnings:
May only have a max of 4 primary partitions per disk - thus a means has to be made to provide  partitioning to re-install ubuntu.
Windows tools for windows problems - linux tools for ubuntu situations -> use windows disk utility to manipulate windows partitions, as windows can be very finnicky. 

Guides to follow :

[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/) 

[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)


Dual booting is set up many times on a daily basis, you should have no problems.
In the event you have questions or require further guidance, by any means - ask.[INDENT]hth <== BDQ

[/INDENT]

---

### Post by unibroker on 2012-10-16
I am just trying to confirm that when advised to do a "clean install" of Ubuntu 12.04 64 Bit that I will only be cleaning the partition that is currently occupied by 12.04 32 Bit.  The WinXP partition is not disturbed.

Yesterday, after burning the 64 bit iso, I booted it from CD to see if the "Something Else" choice was one of my options when I cam to the Try Ubuntu/Install Ubuntu screen.  It was not.  I thought maybe it was on the next screen of Install Ubuntu but I didn't want to start an install process with no escape.  It's been a year since I set up my current dual boot so I can't remember when you're locked into the install process.

---

### Post by Mark Phelps on 2012-10-16
If you're worried about trashing XP, then do yourself a favor and do the following:
1) Download and install the FREE version of Macrium Reflect in XP
2) Run the app and do a backup of XP to an external drive
3) Use the option to create and burn a Linux Boot CD in Macrium

This way, if anything happens to XP, you will have an easy way to reload it from the backup.

---

### Post by unibroker on 2012-10-16
I believe I found my answer in searching for screenshots of the install process.  "Something Else" option comes after choosing Install Ubuntu and you do have a choice to quit the procedure.

---

### Post by unibroker on 2012-10-16
> **Mark Phelps said:**
> If you're worried about trashing XP, then do yourself a favor and do the following:
1) Download and install the FREE version of Macrium Reflect in XP
2) Run the app and do a backup of XP to an external drive
3) Use the option to create and burn a Linux Boot CD in Macrium

This way, if anything happens to XP, you will have an easy way to reload it from the backup.

I only looked for a way to protect my XP install because I have misplaced the key to re-install and don't have the install disc.  The only thing I have related to XP is something I made per instruction when I purchased the desktop I've labeled PC Recovery.  I would guess the installation is in the 3 discs it took to make.  

I think the procedure I read yesterday on this forum should work because the first time I set up dual boot I did nothing to XP other than reclaim some of the drive space it was occupying for Ubuntu (I need to take more which I will do before the clean install of the 64 Bit). 

Thanks for the input.  This forum is an amazing resource!

---

