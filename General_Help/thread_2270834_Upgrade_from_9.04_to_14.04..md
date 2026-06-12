---
title: "Upgrade from 9.04 to 14.04."
date: 2015-03-25
forum: General Help
---

### Post by aviladkar on 2015-03-25
I have Acer One 10 inches laptop. RAM is 2 gb. I am unable to install 14.04 on my laptop. I am having original CD of 9.04. I installed the same successfully. My question is can I upgrade from 9.04 to 14.04. If yes, pls. guide me. And, if not, how to install 14.04? 

Thanks n Regards.

---

### Post by ian-weisser on 2015-03-25
> **aviladkar said:**
> I am unable to install 14.04 on my laptop.
Please elaborate to us a bit more detail.
Is the installer telling you?
Are you getting some kind of error message?
When during the install process?
What does the message say, exactly?

---

### Post by aviladkar on 2015-03-25
i have downloaded the ISO image of 14.04, burned a dvd of the same. When I install from the dvd, everything is fine. But somewhere in the middle, I get an error message that permission is denied, and then everything stops.

---

### Post by grahammechanical on 2015-03-25
As an experiment I recently installed 9.04 on my machine and tried to upgrade to 12.04.. I think I got as far as 11.04 and the user interface became so messed up that I just wiped that installation out of existence. It can be done but it is complicated. You need to go to 9.10 and then 10.04 and then 12.04 and then 14.04. There are big code changes between 9.04 and 11.04 and then further change between 11.04 and 12.04. And change yet again between 12.04 and 14,04. 

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Did you run a Try Ubuntu session? How did that go? What CPU and what graphic adapter does this machine have?

Regards.

---

### Post by Topsiho on 2015-03-26
As far as I know the install of 14.04(.2) is the same as of 9.04, so if you succeed in installing the one, you should succeed in installing the other.
It is very strange to encounter permission problems half-way the install.
I have an Acer One on which I have always installed new versions of Ubuntu successfully, with 1 GB (later 1.5GB) Ram, and an 8 GB SSD. When Unity arrived, however, the Acer One was too slow, and I installed Lubuntu or Xubuntu instead.
Maybe someone on this forum might be able to tell why the permission problems pop up during the install. Did you change your names somewhere somehow? I am just guessing ...

Edited: changed "you names" to "your names" :(

Topsiho

---

### Post by ian-weisser on 2015-03-26
> **aviladkar said:**
> But somewhere in the middle, I get an error message that permission is denied, and then everything stops.
Can you tell us *anything* more?
What is the screen showing?
What is the complete, exact error message?
What was the previous non-error message or dialog or prompt or information?
How many seconds into 'the middle' does it occur?

---

### Post by aviladkar on 2015-03-27
Yes. Initially, when the wubi menu appeard, the name was acer. I changed it to my name, and procedded. Is it because of this I am getting these problems? I tried n number of times, but not successful. This time Ubuntu has given me lot of trouble.

---

### Post by aviladkar on 2015-03-27
Yes. Initially, when the wubi menu appeard, the name was acer. I changed it to my name, and procedded. Is it because of this I am getting these problems? I tried n number of times, but not successful. This time Ubuntu has given me lot of trouble.

---

### Post by Elfy on 2015-03-27
wubi? If you're trying to upgrade that - the main question is why? it was never designed to be more than a way to try ubuntu. 

Do a proper clean dual boot with a supported version.

---

### Post by aviladkar on 2015-03-27
When erroe message appears, it is as follows: - 

An error has occurred.
Permission denied. 
For more information, please see the log file: 
C:\documents1\acer\locals1\temp\wubi-14.04-rev286.log.

When I click OK, everything stops and the installation is aborted.

---

### Post by aviladkar on 2015-03-27
In fact, I downloaded the ISO image from ubuntu site, burned the dvd with infra recorder. But, when I install from this dvd, when laptop boots, it starts as wubi type installation.

---

### Post by aviladkar on 2015-03-27
Means, i should not change username, which appears there.

---

### Post by Topsiho on 2015-03-27
Wubi is not supported anymore. So do a clean normal install, without Wubi :)

Topsiho

---

### Post by aviladkar on 2015-03-27
I downloaded the ISO image from ubuntu site. Burned the dvd, installed on usb. Tried to install ubuntu 114.04 from both. End message is please remove the installation media, and hit ENTER. After that windows starts and usual wubi window appears, where selection of drive, username, password is required to be filled. And then, download of the ubuntu starts. In the midway, somewhere, I get the error message. And then installation aborts. I tried all options, but in vein.

---

### Post by aviladkar on 2015-03-27
In fact, when I burned the dvd, and checked its contents, wubi.exe file is there.

---

### Post by Rex Bouwense on 2015-03-27
As Topshio has already stated, wubi (even though it may be on the install disk) is no longer supported.  If your have a good burn and have checked the md5sum, boot from the install disk that you created and try Ubuntu.  After you insure that everything is working you can install it without re-booting.  You will be given a choice to install it along side of your current Operating System or wipe the disk and install it as the sole Operating System.  In any event you need to back up all of your data because you never know what is going to happen and if you have data that you cannot do without you may lose it.

---

### Post by Topsiho on 2015-03-27
> **aviladkar said:**
> I downloaded the ISO image from ubuntu site. Burned the dvd, installed on usb. Tried to install ubuntu 114.04 from both. End message is please remove the installation media, and hit ENTER. After that windows starts and usual wubi window appears, where selection of drive, username, password is required to be filled. And then, download of the ubuntu starts. In the midway, somewhere, I get the error message. And then installation aborts. I tried all options, but in vein.

I don't get it. You seem to install Ubuntu two times, one normal (is it ???)  install and one inside Windows, using Wubi. No wonder these two installs clash.
I think that first of all within Windows you should uninstall the Wubi install of Ubuntu as this appears to mesh up things, and is useless anyhow (as wubi is not supported anymore).
After that is done you should start the LiveDVD or USB and TRY Ubuntu first, in order to see whether it works with your hardware. If that's OK, then you can install Ubuntu alongside or in stead of Windows, just as you wish. If you still need Windows, then install Ubuntu alongside of Windows.
Let the install program install grub where it proposes to place it, and after that you can start your computer, in Ubuntu, or in Windows, if it still exists, just the way you want it.

Ubuntu is an operating system
Windows is an operating system

Ubuntu is not meant to run within Windows. Not really, but with the wubi install it is made to do exactly that. It is good that Wubi is not supported, and strange that wubi.exe (a windows executable program) still exists. Not your fault :). Anyway: don't use it.

Back up your precious data first. You should have done this a long time ago  already ... but if they are still there, it's not too late yet to do so NOW.

Topsiho

---

### Post by Rex Bouwense on 2015-03-27
+1

---

### Post by Elfy on 2015-03-27
I 'think' that wubi is on the install disc only because it needs to be there as 12.04 (when it worked) is still suppported, I could be wrong. 

You should however ignore it.

---

### Post by hakuna_matata on 2015-03-27
IMHO it is always possible to install Ubuntu 14.04.2 without Wubi and it would be the better solution. But if your alternate decision is that you use an outdated 9.04 with Wubi, here are some informations:

The devs don't produce a wubi.exe for 14.04.1 or 14.04.2 but there is still a wubi.exe on 14.04.1 or 14.04.2 isos. Unfortunately, it is still for 14.04. If you run wubi.exe with internet connection it tries to download a correct iso with old links for 14.04. Then it compares md5sum of 14.04. with md5sum of 14.04.2 which are different. An error occurs and that's it.

A solution is that you can disconnect internet connection during Windows part of installation: [http://ubuntu-with-wubi.blogspot.ca/2014/10/installing-ubuntu-14041-with-wubi.html](http://ubuntu-with-wubi.blogspot.ca/2014/10/installing-ubuntu-14041-with-wubi.html)
Solution is for 14.04.1 but it works for 14.04.2, too.

---

### Post by aviladkar on 2015-03-28
I am having dvd as well usb for 14.04. Can anybody guide me step by step on how to install 14.04 without wubi? Pls. be detail, as I am not much aware of all these technical terms. Thanks.

---

### Post by Topsiho on 2015-03-28
Instructions asked you can find here.
Please read them all first, before the actual install :)

And: it never is as daunting as it seems to be:

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

It says somewhere: 

"You should also make sure you have enough space on your computer to install Ubuntu"

I want to add that you probably should create this space for Ubuntu from within Windows itself, if you decide to keep Windows.
After that you should start Windows again, in order to see whether everything is OK.
If you create this space during the install of Ubuntu, you run the risk that Windows gets confused, and doesn't boot anymore, or takes a very long time to do so and seems to hang.


Topsiho

---

