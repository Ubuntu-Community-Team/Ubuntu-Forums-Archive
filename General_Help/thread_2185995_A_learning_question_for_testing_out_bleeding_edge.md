---
title: "A learning question for testing out bleeding edge"
date: 2013-11-05
forum: General Help
---

### Post by williammanda on 2013-11-05
I'm look for an easy way to test OS, video drivers, mythtv, etc.... My thought is to get the basic OS and any other initial software working....then copy all that to another partition and somehow do something to grub to allow it to boot. The reason for this...I could change the drivers or bleading edge software, some of which are from git, and if it gets borked then I can just copy over that partition with the original partition and start over.
One of the reasons for doing this....some older distro's can take over an hour to install and update...and then you start setting it up

I know this isn't a Ubuntu+1 question but I thought maybe someone is doing what I'm inquirying about.
Thanks

---

### Post by ibjsb4 on 2013-11-05
An option would be to use a virtual machine instead.  This would allow snapshots to take your system back to a previous state with just some mouse clicks.

I find that VirtualBox, downloaded from the vBox site to work well for me.  It runs ok on a dual core box with at least 2G of ram, more ram is better.

[https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by philinux on 2013-11-05
Moved to General Help.

---

### Post by jamesisin on 2013-11-05
It's pretty easy to create multiboot systems with various iterations of Linux (much easier than creating a Windows and Linux dual boot system).  One important thing to remember is you'll need to run *update-grub* after each installation or version upgrade.  (You can fix that if you forget, so that's not even much of a show-stopper.)

---

### Post by williammanda on 2013-11-05
> **jamesisin said:**
> It's pretty easy to create multiboot systems with various iterations of Linux (much easier than creating a Windows and Linux dual boot system).

Please give more detail so I may better understand.

> **jamesisin said:**
> One important thing to remember is you'll need to run *update-grub* after each installation or version upgrade.  (You can fix that if you forget, so that's not even much of a show-stopper.)

From my experience after each install *update-grub* is performed automatically.

---

### Post by jamesisin on 2013-11-05
You can find dozens of tutorials and how-tos on the Web for multibooting using Linux.  Google is your friend.

If you have specific questions, we'll be happy to help.

---

### Post by williammanda on 2013-11-07
> **jamesisin said:**
> You can find dozens of tutorials and how-tos on the Web for multibooting using Linux.  Google is your friend.

If you have specific questions, we'll be happy to help.

From wikipedia:
Multi-booting is the act of installing multiple operating systems on a computer, and being able to choose which one to boot when starting the computer.

Is this your definition of multibooting? If so...how does this help / answer my original question?
Thanks

---

### Post by jamesisin on 2013-11-07
You want to boot into the original and then into the copy.  That's multibooting.  You need to be able to switch between multiple boot environments.  Your use of this is perhaps a bit unique, but it relies upon the same underlying structure.  In your case instead of choosing between Ubuntu 12.04, Ubuntu 13.10, and Mint 14; you'll be choosing between Ubuntu 12.04 with properties X and Ubuntu 12.04 with properties Y (or whatever).

---

### Post by williammanda on 2013-11-07
I want to get the main focus back...
The main point is....
I want to copy one partition that has a known working OS over to another partition so that I can experiment with it without effecting the 1st partitions OS. This is the most important issue at this point that I would like to resolve with the best option.
Thank

---

### Post by grahammechanical on 2013-11-07
I actually think that this is very much a Ubuntu+1 question because it relates to the question of how to set up Ubuntu+1 testing . May I tell you my way of working? I have at the moment 3 Trusty Tahr installs as well as a 13.10 and a 13.04 and a couple of the Ubuntu flavours.

we need to create at least one additional partition of about 10 - 15GB. You can do that from a live session using Gparted which will be in the Dash. Then we install a daily ISO image into that partition using the Something Else option. And there we are testing! We have tested the installer and the reboot into a working Trusty Tahr (or may be a not working Trusty Tahr). We also have a default installation of Ubuntu that we can install experimental software on such as proprietary video drivers & Linux kernels. If something breaks then we can just re-install. There is no need to clone. Just put in another installation of Ubuntu. It really does not take that long.

We can also test by simply using the software and updating every day until Trusty Tahr becomes Ubuntu 14.04. A couple of days ago an update brought in Ubuntu Web Browser, also known as, Browser. It is the browser that will be on Ubuntu Phone but it is running on Ubuntu desktop and I am trying it out. You need to learn how to install Ubuntu into separate partitions. You can get the ISO images from here

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds)

This link will help you find your way
[URL="http://www.theorangenotebook.com/"]
http://www.theorangenotebook.com/[/URL]

Regards.

---

### Post by Bucky Ball on 2013-11-07
> **williammanda said:**
> 
The main point is....
I want to copy one partition that has a known working OS over to another partition so that I can experiment with it without effecting the 1st partitions OS. 

Remastersys:

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

You can create an ISO of your current install, with or without your personal data, create install media from it, and install it to another partition (or five hundred other machines). Two identical installs.

Or:

[https://duckduckgo.com/?q=clone+current+install+ubuntu](https://duckduckgo.com/?q=clone+current+install+ubuntu)

There's plenty of info out there. Have a look.

---

### Post by williammanda on 2013-11-15
Thanks for all the replys!
I have found a simple and quick method that makes sense.

How to create a copy of an existing installed OS

1. Live boot Parted Magic or equilient 
2. Open root terminal and enter command:
rsync -av --stats --delete /media/sda3/ /media/sda7/
3. Run Grub Doctor. Select /media/sda7 as the first entry in the grub boot menu. Select sda to install grub.

This took all of 7 minutes to complete with sda3 = 9GB.

Once done, I have a clone of the OS and software installed on sda3 on sda7. I can now experiment on sda7 without regard of screwing up.

---

### Post by Bucky Ball on 2013-11-15
If you now consider issue solved, please mark the thread as solved by following the instructions in my signature. Thanks.

---

