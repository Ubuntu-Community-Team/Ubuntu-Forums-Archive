---
title: "Wireless, graphics driver, and poor performance problems"
date: 2013-04-02
forum: General Help
---

### Post by rnadmoiezd on 2013-04-02
[FONT=arial][COLOR=#000000]Ok, I'm sorry for compiling all of them into one section but it seems so much more efficient to do it this way. Here is what I'm having problems with (keep in mind I'm relatively newbish):[/COLOR]

[COLOR=#000000]1. My wireless internet keeps dropping. It stays connected (so it says) but actual internet functionality goes out the window. After a while it asks for my network password. Upon entering it, it does nothing. The only fix is to unplug my adapter and plug it back in. I've tried downloading the drivers converted the .tgz with alien, trying to install and also tried following instructions from users here who have had the same problem installing drivers for it but I have not been able to successfully install them. [/COLOR]**The adapter is an ASUS N-13 USB.**

2. For the life of me I cannot get my graphics drivers to install. The computer works (kinda) I can see the screen but every now and then the text "blurs" out and pictures also. Very weird. I have also downloaded the .run file and have not been able to install sucessfully. Maybe I don't have the right one. I don't know. It says it has to install as root and then disappears forever.** The card is an Nvidia Geforce GTX 550 ti by EVGA if that matters.**

3. And lastly the computer is SLOW. Ungodly slow. It shouldn't be considering I have an i5 with 8gigs of RAM. Not the greatest, I know, but not shabby either. FWIW in comparison Windows is very close to being 10x faster. I have seen Ubuntu in action and know it is not this slow.

I really love Ubuntu and would like to switch to it almost full time. I'm done with Windows and would like to learn something new. However, I've been scouring the internet for 3 days digging through forums and articles trying to fix these problems. You guys are really my last hope for this OS.[/FONT]

---

### Post by xSadoro on 2013-04-02
Well I am not the best in Linux or Ubuntu at all, but I think it is slow because you graphics card have not been installed yet (which should not be hard to find on Nvidia's official website). And btw , an important question. Did you download the 32 or 64 bit version of Ubuntu? Because with more than 4gb of RAM you require the 64 bit version. As of the adapter / wireless internet I have no idea, you can always reboot your computer , (press shift if you are not automatically run to the grub menu) get in the grub menu and select the option "Ubuntu...(Recovery mode)" And then run the option that says: "Repair broken packages" . If this doesn't work, please wait for other more experienced people to come and help you.

And btw , is yours a laptop? Because I have tried to look for your card's driver.

---

### Post by rnadmoiezd on 2013-04-02
I downloaded what I thought was the drivers for my card. It is a desktop. It was a .run file so I selected to execute it as a program and ran it in terminal. Terminal told me it needed to be run as a root user so I hit enter (the only option) and then nothing happens. I downloaded the driver from here and it is the right one.[http://www.nvidia.com/object/linux-display-amd64-310.44-driver.html](http://www.nvidia.com/object/linux-display-amd64-310.44-driver.html)  My card is listed as supported devices. I got the 64 bit version which is what I'm running. Ubuntu 12.10 64 bit.

---

### Post by wildmanne39 on 2013-04-02
I will try to help with the wireless issue if you start a new thread for the wireless issue and post the link here.

Each thread is supose to have only one issue per thread.
Thanks

---

### Post by CatKiller on 2013-04-02
Installing stuff from some random website is such a Windows thing. Instead, you should have a widget on your panel that tells you there are drivers available for which we don't have source code. If that isn't there, because you've already dismissed it or whatever, pressing Alt-F2 and running **software-properties-gtk** (or selecting **Software Sources** from System Settings, since it's the same thing) and clicking on the Additional Drivers tab will let you select an appropriate driver for your card.

Or you could open a Terminal and run ```
sudo apt-get install nvidia-current
``` if you prefer.

---

### Post by rnadmoiezd on 2013-04-02
OK, sorry about that. Then lets focus on the graphics drivers in this thread. I tried the install current from terminal in a previous attempt but had no luck.

Thread for the wireless problems is here: [http://ubuntuforums.org/showthread.php?t=2131781&p=12585726#post12585726](http://ubuntuforums.org/showthread.php?t=2131781&p=12585726#post12585726)

---

### Post by 3rdalbum on 2013-04-02
Catkiller is correct. Install the Nvidia driver the way they suggest, not the way you were trying.

Ubuntu seems slow at the moment because it is trying to do software 3D rendering. When you have the graphics driver installed it will speed up to the level you would expect.

---

### Post by 3rdalbum on 2013-04-02
With the wireless, you could try limiting the speed. Run this in the terminal whenever you start up and see if it helps:

sudo iwconfig wlan0 rate 11M

---

### Post by rnadmoiezd on 2013-04-02
Ok, I did it the way that was suggested. It never worked the few times I tried it that way but this way it did (I think). The computer has sped up a good bit. Still not as fast as Windows, but at least tolerable now. However, in the system details it still shows my gpu as "unknown". Is it still supposed to still say that after I installed? As for the wireless issues please see the other thread listed here: [http://ubuntuforums.org/showthread.php?t=2131781&p=12585726#post12585726](http://ubuntuforums.org/showthread.php?t=2131781&p=12585726#post12585726)

---

