---
title: "black screen on bootup"
date: 2007-11-15
forum: General Help
---

### Post by agmatwot on 2007-11-15
Hello, 

I'm a complete ubuntu noob, and I need help getting up and running.  It appeared to install just fine.  When I chose ubuntu from the boot menu, it starts to load, then my monitor loses signal for about 30 sec, then it continues to load.  Then the screen goes black, monitor is receiving a signal, but it's just black.  I've read many suggestions on this forum, but nothing works.

ctrl+alt+F1 does nothing
hitting esc right after i select ubuntu to get safe mode does nothing.
No combination of keystokes does anything at all.  
I tried to switch monitors, no change.

I have a ATI X1650XT, my computer has an onboard nvidia chip that can't  be disabled in the BIOS, only in windows. (go figure)  It's the only thing i  can think of that could be causing a video problem.

how can i fix a problem when I can't perform any inputs whatsoever?

thank you for your help.

---

### Post by mdpalow on 2007-11-16
I'm not clear on one thing. You are trying to run the Live CD, so you can get it up and running to install or you've already installed it and the screen goes blank?

If not installed yet, try the second option with the Live CD boot. When I tried the first option the same thing happened to me. 

If already installed, did you install with a CAT5 connection to the internet? If not, you should always install Ubuntu with an Internet connection, so it can download drivers. 

Not great advice, but hopefully something to get you started. Also, if that doesn't work, then it might be something more complicated with your ATI card.

good luck...

---

### Post by agmatwot on 2007-11-16
I don't have a live CD, I installed it via the downloadable setup program.    All I did was run the .exe.  As i said, it appears to have installed just fine.

---

### Post by bikerjeg on 2007-11-16
I'm having a similar problem with my hp pavilion 6470us

I have ubuntu installed via wubi and when I select it from the boot menu it seems to load but then all I see is a black screen after a while. I have not tried anything yet but I don't know what to do.

I had a similar problem trying to install 7.10 from a live cd I burned, but it would go to a black screen after I selected to install so I was not able to install 7.10 from the cd at all.

---

### Post by mdpalow on 2007-11-16
> **bikerjeg said:**
> I'm having a similar problem with my hp pavilion 6470us

I had a similar problem trying to install 7.10 from a live cd I burned, but it would go to a black screen after I selected to install so I was not able to install 7.10 from the cd at all.

Yeah, I had same problem and then used the second option after running the live disk. I forget what it's called, but it's some video recovery mode or something like that. I can't remember what it says...

that one works and if the screen goes black again, try moving your mouse...

For the original poster, is there any other install option you can select when doing it on-line? Also, is downloading the Live CD and trying that an option for you?

Good luck guys....

---

### Post by bikerjeg on 2007-11-16
> **mdpalow said:**
> Yeah, I had same problem and then used the second option after running the live disk. I forget what it's called, but it's some video recovery mode or something like that. I can't remember what it says...

that one works and if the screen goes black again, try moving your mouse...

For the original poster, is there any other install option you can select when doing it on-line? Also, is downloading the Live CD and trying that an option for you?

Good luck guys....

I tried the low res, second option you mentioned but that did not end up working either. It does the same as the first option on the live cd, it looks likes it's installing but then after the install goes through a few processes the screen boots into a blank screen and moving the mouse won't do anything. --by the way my live cd is for 64bit amd

---

### Post by jetset125 on 2007-11-29
Hi there, I am a new linux user so I may not be correct on this suggestion, but have you tried switching your monitor's connection? 

I have a dual monitor set-up and found that it only uses VGA as a primary display, and leaves my other monitor (connected via DVI) connected with a blank screen. Even when I hooked my computer up to a single monitor via DVI w/o the VGA connection I got a blank display.

I have the same card you do so why not try it out?

It might be that the your video adapters are conflicting and trying to only display using what linux thinks is the primary display adapter. 

Just a thought.

---

### Post by iceblue on 2007-12-15
I got exactly the same question when booting up.

My Computer :

CPU : Athlon 64 X 2 3600 +
Mainboard : Gigabyte GA-M55S-S3 (Chipset nForce 550)
Display Card : ATi X1550
Monitor : 1440 X 900 widescreen
Ram : 512mb X 2 running Dual Mode

I can successfully run Ubuntu both with the 6.06 LTS (PC  version) and 7.10-desktop-i386 Live CD. Howerver, after installing Wubi-7.10-alpha-rev386 + ubuntu-7.10-desktop-i386, with the noapic error fixed (edit the Kernel manually), it goes blank screen after startup  message shows for a few sec, the normal case I supposed will be a loading bar appears right after but it doesnt show up, I just dont know how to fix it. Is it better to do a partition (eg drive W) to do the setup again ? Gracis.

---

### Post by iceblue on 2007-12-15
I tried 2 more things to enter Ubuntu

A.Using the 7.10, Kernel 2.6.22-14 generic (recovery mode)

1. [email]root@administrator.desk[/email]top:~# startx
2. when entered into window, message appears, "This session is running as a privileged user"
3. press "continue"
4. error message "user switcher"has quit unexpectedly, if you are load a panel object, it will automatically be added back to the panel"
5. press "reload" nothing happen, press"dont reload"bypass the message.

Even I can run Ubuntu under Recovery mode, it just cant connect to the internet.

B.Using the Normal mode

1. press "esc" when starting up
2. press "e" to edit the Kernel with the noapic problem

loop/ubuntu/disks/root.disk ro quiet splash 
loop/ubuntu/disks/root.disk ro quiet splash noapic < add this command)

3. press "b" to boot
4. when trying to go to Ubuntu, the system light flash for awhile, (seems to load something), then it turns into blank black screen with no cursor or anything, and the light no longer flash.

With the Recovery mode I can enter the sytem but no internet connect, and with the Normal mode I cant even run Ubuntu and got a black screen in turn, I dont know where is going wrong and dont know how to fix it.

Hope someone out there can blad me out. Gracis.

---

### Post by ago on 2007-12-17
Does the screen go black during boot and then you see a normal desktop, or does it goes black and stays black?

In the first case it's likely an issue with usplash resolution
In the second cas it's usually a missing graphic driver

---

### Post by iceblue on 2007-12-23
> **ago said:**
> Does the screen go black during boot and then you see a normal desktop, or does it goes black and stays black?

In the first case it's likely an issue with usplash resolution
In the second cas it's usually a missing graphic driver

Thank so much for your help. I tried to install Ubuntu 7.10 again today (without Wubi), using a usb harddisk(sda) and the Live CD (AMD64 Desktop).  When starting up, I edited 2 things in the Grub.

1. add noapic
2. remove splash
3. the kernel from ...... /root.disk ro quiet splash becomes
                              ..... /root.disk ro quiet noapic  <----remove the splash

Finally I can go into Ubuntu window !  No hardware has been modified.  Here is my computer hardware.

CPU : AMD Athlon 64x2 3600
Chipset : nForce 550
Harddisk : PATA 80G
Display Card : Sapphire X1550 (ATi)
LCD : 1440 x 900 wide screen

I think that it's better to modify the menu.lst so that it wont be necessary to edit the Kernelduring next startup.

Thanks again for your Help !

---

### Post by Anthaneezy on 2008-01-18
I was having the same problem. I'm using a Dell Optiplex GX260 with onboard video. I powered down my system to install a new hard disk that I was recovering data from. After finishing my work and performing a graceful shutdown and reboot, the Ubuntu with the [ | | | | | | ] progress bar would fill up, then my screen would go black. Obviously it wasn't my hard disk change as it was reading my Ubuntu install correctly. I tried using the boot parameter "no-hlt", didn't work. I was about to try the aforementioned "noapic" parameter so I powered down my system. I also pulled the machine out and made sure all the connections were plugged in and tight. All were, except my network cable. So I plug that in, and continue tightening all the other connectors. I reboot the computer while on the ground and I miss pressing ESCAPE so it boots into Ubuntu. Except this time it goes in successfully! I'm not saying it's a fix, but somehow having an unplugged network cable caused Ubuntu to hang. Possibly a network service that assumed a connection that was there and just waited.

---

### Post by Aloshi on 2008-01-20
I've been having the same problem using Wubi 7.10.  Wubi 7.04 installed fine, except stupid me tried to upgrade it, thus breaking XP and Ubuntu (Tried loading up Ubuntu, then did hardreboot, BOOM goes the computer).  Recovered from an XP Install CD and downloaded Wubi 7.10, put the desktop ISO in the same folder, thought it installed fine. I pressed the power button on my computer once after letting Ubuntu try and boot for about 5 minutes. However, when I pressed the power button, all of a sudden the display jumped to life! It seemed a hardware detection thing was going on (it showed for a brief second) then did a shutdown.  XP is still intact, I'm going to try uninstalling then reinstalling Wubi.

Oh, and I have been trying to just install Ubuntu 7.10 from a Live CD (that I spent 8 hours trying to get working).  Once I finally was able to boot into Ubuntu from it, I tried to install, but I can't manage to get my Windows partition resized so I have enough free space to create a new partition. (See [this]("http://ubuntuforums.org/showthread.php?p=4170297#post4170297")).

---

### Post by pliktrologos on 2008-02-15
> **jetset125 said:**
> Hi there, I am a new linux user so I may not be correct on this suggestion, but have you tried switching your monitor's connection? 

I have a dual monitor set-up and found that it only uses VGA as a primary display, and leaves my other monitor (connected via DVI) connected with a blank screen. Even when I hooked my computer up to a single monitor via DVI w/o the VGA connection I got a blank display.

I have the same card you do so why not try it out?

It might be that the your video adapters are conflicting and trying to only display using what linux thinks is the primary display adapter. 

Just a thought.
I'm having the same problem here. I'm a newbie, I'm sorry for my bad English and I hope you can figure out what I am describing. I had this problem also with a clean install on Feisty, as the clean install now on Gutsy. The screen goes black always after the boot loader and until the login screen if my LCD monitor is connected via the DVI, but NOT if it is connected by the analog cable (that's the one with the 15 pins). I've tried installing Gutsy with all 3 possible types of connection (1. with only the DVI cable, 2. with only the analog cable, 3. with both analog and DVI cables connected) and always with internet connection available during setup but nothing changed. My pc's hardware configuration can be viewed in my signature. After installing the Gutsy I also tried to configure the kcontrol (monitor & display tab) with 2 monitors and different resolution on each one cause the primary is 17" DVI and the secondary is a 15" analog but I couldn't extend my desktop :(

---

### Post by ke4ram on 2008-02-15
A couple of kernal updates ago I encountered a similer problem. 

The computer boots normally, I get the first screen, then just before the icons are brought up it 'Blanks out'

Move the mouse, hit a key and it's back. No problems whatsoever after that. Figured they would get around to fixin it but not yet. 

Running an older athalon with an older nvidia vidcard. 

I like ubuntu, hope these upgrades don't ruin it. Haven't booted billy
(MS-XP) for over six months now. Kinda nice

---

