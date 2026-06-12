---
title: "Ubuntu 14.04 LTS questions?"
date: 2015-04-24
forum: General Help
---

### Post by Yezinki on 2015-04-24
I want to dual boot W7 32 bit with Ubuntu 32 bit but am concerned about issues I might get later, if may be.

1. Should W7 be installed, updated and back up image created just in case, if machines messes up, grub issues etc, at least would have W7 and all my personal data, research?

2. How should the 320 GB HD be partitioned for both?

3. Which OS should be installed 1st?

4. Is it better to install 1 OS on 1 machine, since both are W7 Pro and Ubuntu 14.04 LTS 32 bit compatible?

5. The only reason that is keeping me away from dual boot is that don't want to be the forums 24/7 for assistance. Plus both my machines have no option for a usb boot.


That said plan to install Ubuntu 32bit  ONLY on my weaker machine i.e Sony T2400 CPU on which years back ran Ubuntu 12.

a. How do I partition the 320 GB HD?

b. Is 50 GB for / ext4 Primary Beginning, 4 GB swap end of drive and all rest to /home Logical ext4 Beginning of the drive fine?

c. You experts care to edit?

d. The reason for installing on it is that has a 32 bit CPU, Intel on board graphics no vid card, and only 2 GB of memory RAM. Plus I know is compatible with Ubuntu since ran 12 fine.

Hoping to hear your thoughts.

Thanks.

---

### Post by nerdtron on 2015-04-24
For starters, assuming "only" window  7 is installed, and no dual boot at the moment.

First, backup your important data to another computer/usb/hard drive/etc. This is important everything you install any os or manipulate partitions, there is always a risk of losing your data.


Next, burn the iso image of Ubuntu to a DVD disc. Then boot from CD.
Once Ubuntu boots, on the installation screen, it will offer you to "Install Alongside Windows 7". You will also have the ability to set the size allocated for ubuntu on the next screen after that. Maybe 50 GB is good enough.
You don't have to define/edit partitions manually. Ubuntu installer will take care of that.

---

### Post by Yezinki on 2015-04-24
> **nerdtron said:**
> For starters, assuming "only" window  7 is installed, and no dual boot at the moment.

First, backup your important data to another computer/usb/hard drive/etc. This is important everything you install any os or manipulate partitions, there is always a risk of losing your data.


Next, burn the iso image of Ubuntu to a DVD disc. Then boot from CD.
Once Ubuntu boots, on the installation screen, it will offer you to "Install Alongside Windows 7". You will also have the ability to set the size allocated for ubuntu on the next screen after that. Maybe 50 GB is good enough.
You don't have to define/edit partitions manually. Ubuntu installer will take care of that.


Thanks for replying with your expert views.

Just too confused.

1. Ubuntu on tried weaker machine and W7 on the other?

2. If Dual boot why along side not guided?

3. Does one need BCD for dual boot?

Thanks?

---

### Post by yancek on 2015-04-24
Whether you put Ubuntu on one machine and windows on another or put them both on one machine is basically your choice.   Installing new operating systems and creating/modifying partitions is always risky regardless of what operating system you may be installing/changing so you need backups if you have anything you need.  Separate machines if you have them and if your experience is limited would be safer.

The Alongside option if shown will be simpler as the user doesn't have to make choices.  The bad part of it is that it is somewhat automatic and if something does go wrong, you won't have any idea what it was.  Using the Manual option which is referred to as "Something Else" will give you more control.  If it has been a while since you have done an install, you might review some tutorials on it.  The first link below is to the ubuntu.com site and gives a very simplified version of installing using the "Alongside" method.  The second link is much more detailed and gives excellent information on Linux in general as well as partitioning.  If you scroll about half way down the page, you will see a step by step guide.

 [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

I'm not sure what you mean by your question about BCD.  Are you referring to you manually modify the bcdedit file on windows to create an entry to boot Ubuntu?  I have no idea how to do that and I expect that is not what you mean.  If you are instead referring to EasyBCD, it is basically a graphical front end to a modified bootloader they created called neogrub which in turn is a modification of software called Grub4Dos which is a modification of the actual Grub bootloader.  The original Grub usually works better to chainload other operating systems but this again is a user choice.  Either should work if you are only planning on having the two systems.

---

### Post by Yezinki on 2015-04-24
> **yancek said:**
> Whether you put Ubuntu on one machine and windows on another or put them both on one machine is basically your choice.   Installing new operating systems and creating/modifying partitions is always risky regardless of what operating system you may be installing/changing so you need backups if you have anything you need.  Separate machines if you have them and if your experience is limited would be safer.

The Alongside option if shown will be simpler as the user doesn't have to make choices.  The bad part of it is that it is somewhat automatic and if something does go wrong, you won't have any idea what it was.  Using the Manual option which is referred to as "Something Else" will give you more control.  If it has been a while since you have done an install, you might review some tutorials on it.  The first link below is to the ubuntu.com site and gives a very simplified version of installing using the "Alongside" method.  The second link is much more detailed and gives excellent information on Linux in general as well as partitioning.  If you scroll about half way down the page, you will see a step by step guide.

 [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

I'm not sure what you mean by your question about BCD.  Are you referring to you manually modify the bcdedit file on windows to create an entry to boot Ubuntu?  I have no idea how to do that and I expect that is not what you mean.  If you are instead referring to EasyBCD, it is basically a graphical front end to a modified bootloader they created called neogrub which in turn is a modification of software called Grub4Dos which is a modification of the actual Grub bootloader.  The original Grub usually works better to chainload other operating systems but this again is a user choice.  Either should work if you are only planning on having the two systems.


Thanks for your very detailed expert reply which has cleared my confusion.

1. No dual boot.......Ubuntu on the one which I used it earlier some years back Ubuntu 12.04.......though its a weaker machine but tried and tested.

2. Yes I meant Easy BCD........thanks again for the detailed explanation.

So I restart my journey installing Ubuntu 14.04 32 bit LTS on Sony T2400 @ 1.8 GHZ, 2 GB RAM, Intel graphics, 320 HD using guided, /50 GB ext4 Primary Beginning of drive, swap 4 GB end of drive and the rest /home ext4 Logical Beginning of drive.

---

### Post by dragonfly41 on 2015-04-24
At the start of your journey make a Windows 7 recovery disk to recover Windows in the event of mishaps.

[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc?](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc?)

You could create a remote backup for some files via SpiderOak.

[www.spideroak.com](www.spideroak.com)

You could create a Firefox sync account for Firefox data (bookmarks etc.)

Re: suitability of Sony T2400 CPU  .. check tips in this sticky thread ..

[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by Yezinki on 2015-04-24
> **dragonfly41 said:**
> At the start of your journey make a Windows 7 recovery disk to recover Windows in the event of mishaps.

[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc?](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc?)

You could create a remote backup for some files via SpiderOak.

[www.spideroak.com](www.spideroak.com)

You could create a Firefox sync account for Firefox data (bookmarks etc.)

Re: suitability of Sony T2400 CPU  .. check tips in this sticky thread ..

[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

Thanks for your expert reply and posted links.

1. I  aint dual booting only Ubuntu 32 bit.

2. Have created a back up, just in case, gonna clean install Ubuntu only.

3. Ran Ubuntu 12.04 LTS on the same machine T2400 CPU so should work fine.

Shall keep you updated.

Thanks again.

---

