---
title: "Dual boot &amp; keyboard problems with a medion akoya p2214t hybrid notebook tablet"
date: 2014-10-06
forum: General Help
---

### Post by Robert Gibbins on 2014-10-06
Recently I bought the **Medion Akoya P2214T Hybrid Notebook/Tablet** from Aldi. It comes with 64 bit Windows 8.1 Upgrade already installed.  Software one Windows tech writer recently described as 'the worst operating system ever'.  The sales and activation statistics would seem to bare that out. Vista for all its problems for instance through out its corresponding life-cycle has consistently out sold it.  With that in mind and the fact that I am a long times Linux user I wanted to do is install the  64bit version of Ubuntu 14.04 version on my new computer. I also realise that Ubuntu 14.10 is due out on the 23 October 2014. To that end I installed Ubuntu onto a USB stick and did a live install to try it out on the Medion.

 The installation at first glance all worked well. The Touch Screen worked in a limited way considering Ubuntu Touch has not been full implemented yet. I was able to open folder, windows etc. and move them about with my finger. I was even able to open LibreOffice with the touch of my finger. I was able to connect the WiFi and download VLC. I was also able to connect and operate a Bluetooth Keyboard.  The TouchPad also worked along with a standard USB keyboard. However, there was one exception the Ubuntu software **couldn't access ****or find**** the** **DockingStation Keyboard**.
 As temporary approach to the keyboard problem I then attempted a dual OS installation; Windows and Linux. That failed mainly because Ubuntu during the installation phase failed to find the installed version of Windows 8.1 no matter what I tried.  It has to be remembered that this computer comes with a 500 gig hard drive in the docking station and a 65 gig SSD in the tablet part of the machine. What ever way I tried to install Ubuntu however it could find the Windows system. So at this point I am at a lose. I don't know whether to keep the computer or save the aggravation and return it. **Does anyone have any ****ideas, thoughts or ****solutions to the Docking Station Keyboard  ****and or the dual booting problems****? **

One other query while I am here. Running in the Tablet mode does this version 14.04 or it successor of Ubuntu have an on board or virtual keyboard that can be activated. If yes, how is this done?
 I am sorry if this query is appearing in the wrong part of the Forum.  I did write about my concern about the keyboard problem to the Hardware Section of the Forum and to this date I have had 141 views and no replies.  As a result of this I thought I would open it up.
 If anyone has any thoughts, comments or suggestions feel free.  Thank you.
 Robert

---

### Post by grahammechanical on 2014-10-06
There is not much I can say. Ubuntu has an onscreen keyboard. It is installed by default and called Onboard. I think that it is possible to activate it at the login screen. It is certainly possible to activate it after login. It is in System Settings>Universal Access.

As regards the problem with not being able to install, it all depends on whether that device has BIOS or UEFI and MBR partition table or GPT. It could simply be that the 65 GB SSD has 4 primary partitions and with MBR partitioning we cannot have more than 4 primary partitions and if that is the case then the installer will not get very far.

There can also be issues with UEFI, especially with Windows 8 pre-installed. Have you read this?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You say a lot but give very little information that can be used to diagnose either of the problems.

Regards.

---

### Post by Robert Gibbins on 2014-10-07
Thank you for you quick reply.  I was unaware as to exactly what you needed  to know.  I am sorry about that.  By-the-way; because this is a new machine it has UEFI boot and the Intel Fast Boot is also turned off.  I will check the drive partitions details and get back to you tomorrow. 

Robert

---

### Post by Robert Gibbins on 2014-10-07
grahammechanical Hi

I have managed to take some photos of the Medion computer with Ubuntu loaded as a live distribution.
 [ATTACH=CONFIG]257029[/ATTACH][ATTACH=CONFIG]257031[/ATTACH][ATTACH=CONFIG]257032[/ATTACH]

The first photo shows the BOOT MENU.  
Boot Configuration

First Boot                             (Disabled)
Boot Option Priorties
Boot Option #1                      (UEFI: Verbat imStore...)
Boot Option #2                      (Windows Boot Manage..)

The other two photos show the DeskTop.  It seems from the desktop icons that 65 gig SSD has three partitions, Windows 8.1, Recovery, etc and two partition on the 500 gig hard drive. Is this all you need to know?  How does this effect how a dual system can be installed or should Ubuntu just be installed as the sole operating system and how?  I still have the Docking Station Keyboard problem to overcome also.

I hope all this is of some use and you can help me.  Thank you again.

Robert

---

### Post by Mizuti on 2014-11-18
Hi Robert,

Did you manage to find a solution to the keyboard problem?
I bought the same laptop and am running into exactly the same problems you did. I have tried Ubuntu, OpenSuse and Fedora, but all of them give the same behaviour: everything works fine, except for the keyboard.

---

### Post by splint2 on 2014-11-21
Hello,
I bought this Notebook for a few days and had the same problem.
The solution is easy: Follow the entry in Suse-Forum [https://forums.opensuse.org/showthread.php/473200-usb-gaming-mouse-04d9-a078-not-working-linux-plus-workaround](https://forums.opensuse.org/showthread.php/473200-usb-gaming-mouse-04d9-a078-not-working-linux-plus-workaround)
I have increased the HID_MAX_USAGES to 65536, recompiled the kernel and a working keyboard.
Good luck, splint

---

### Post by Mizuti on 2014-11-21
Thanks so much for your help. I will most definitely give that a try. 
But before I mess up, what is the simplest way to recompile the kernel? I have no experience with this. (EDIT: I am currently running Ubuntu 14.10 by the way)

---

### Post by splint2 on 2014-11-22
Hello Mizuti,
I´'&#7743; using Fedora. A simple HowTo is there: [https://fedoraproject.org/wiki/Building_a_custom_kernel](https://fedoraproject.org/wiki/Building_a_custom_kernel). Look at the Ubuntu forum and you can find such a howto for ubuntu.
Greetings, splint.

---

### Post by Mizuti on 2014-11-22
Dear splint
It worked! Thanks again. I was almost about to give up hope of finding a solution.

---

