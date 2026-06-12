---
title: "Resources for help"
date: 2008-05-12
forum: General Help
---

### Post by dmunk on 2008-05-12
Hello,

I'm trying to switch from a Mac to Linux and have been struggling getting the graphics on my notebook situated.  I haven't been able to get much response from my posts - being new to the Linux community, I probably am not articulating the issues clearly.

Are there any other suggested forums/websites to try for help?  I would like to  stay with Ubuntu.

Thanks.

---

### Post by zenwalker on 2008-05-12
Well there r millions of docs avail on Linux in general. All most all of em suits u r problem. And works out on Ubuntu. 

But u need to be specific on the problem u r having.

U said u cant get graphics, that means either u r h/w isnt supported or else u have not installed a graphical system.

No problems.

Download Ubuntu or any Linux distro such as Zenwalk (ZenLive) and run the system with the cd in, test u r system with the live cd first before trying it out on 2 the HDD. 

Any ways, plz give u r machine specs here. Then we shall know if its supported or not. And be more clear on ur problem.

---

### Post by dmunk on 2008-05-12
Included is a text from a previous post, it may not be complete enough, however  I have been trying to make them as comprehensive as possible.  I had attached the xorg.conf and Xorg.0.log to the original post.  [http://ubuntuforums.org/showthread.php?t=789981](http://ubuntuforums.org/showthread.php?t=789981)

 Thanks.

--snip--
I've been able to get Gutsy running on my Lenovo U110, except that I can't seem to get the graphics working entirely (or suspend, but I'm not worrying about that yet).

I was able to use the Live CD with 800x600 resolution. I installed and updated everything and then ran

sudo dpkg-reconfigure -phigh xserver-xorg

which detected the Intel video card – it has the X3100. xorg.conf looks fine to me, but I can't get anything higher than 800x600. I took a detected modeline from the Xorg.0.log file for the desired 1366x768 resolution and put it into the xorg.conf file, but it didn't make any difference.

Any help would be really appreciated.

Thanks.

---

