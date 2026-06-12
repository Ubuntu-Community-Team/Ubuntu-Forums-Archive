---
title: "Will not load ubunut after grub selection"
date: 2007-07-29
forum: General Help
---

### Post by supersnake83 on 2007-07-29
Hi everyone.

I am new to Ubuntu. I have a custom built desktop and I have an ATI Radeon X1300 Pro graphics card. I just installed ubuntu 7.04 using the alternate install.

My problem is I cannot load the desktop. I have downloaded the ati linux driver for my graphics card, but I don't know how to install it since I cannot get into ubunutu. I am using my Vista partition to use this support forum.

Please, if anyone can help, please reply. Again,this is all new to me and I am very interested, so if anyone decides to post directions, please be as detailed as possible, because I probably won't initially know how to do things.

Thanks in advance for any help and sorry I spelled ubuntu wrong in the title,

Geoff.

P.s.

Here are my sysem specs just in case you need to know anything:

Intel E6300 1.86 core 2 duo processor
Intel D975xbx Motherboard
4 gigs of DDR2@ dual channel ram
3x 250 gig Sata 3.0gb/s HDD's
2x 18X DL DVD-RW wirters (one lightscribe writer)
2x Ati X1300 graphics card in crossfire setup (software crossfire, not hardware)
500 Watt PSU
Zalman CNPS 9500AT CPU cooler
and three cooling fans

---

### Post by Paul S on 2007-07-29
ATI video card(s) are your problem.  And two of them may be worse!

You might be able to edit your /etc/X11/xorg.conf file to use the "vesa" driver, so you can boot up.

Are you able to get to the terminal using Control-Alt-F1 keys?  If so, please boot into your ubuntu, go to the terminal, and copy the files /etc/X11/xorg.conf and /var/log/Xorg.0.log to your windows, then post them here.  With these files, we may be able to help you.

regards,

---

### Post by Immolatus on 2007-07-29
ubunut?:lolflag:

---

### Post by Paul S on 2007-07-29
If you are not able to work at the command line in feisty, then I would suggest you try the "edgy" version of ubuntu and see if you can install it from it's livecd.  This was the easiest way for me.  But, I only had one ATI card.  The edgy cd is here:

[http://releases.ubuntu.com/6.10/ubuntu-6.10-desktop-i386.iso](http://releases.ubuntu.com/6.10/ubuntu-6.10-desktop-i386.iso)

If you can, then after installing, you can upgrade to "feisty".  Upgrade notes are here:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Then after upgrading to feisty, you will have to install the latest fglrx driver from ati, following the wiki:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

HTH

---

### Post by supersnake83 on 2007-07-29
Thanks,

And no, I cannot boot into ubuntu. It will load and I will see a lot of text and "ok's" at the right, but then my monitor will refresh to no signal.

Speaking of ok's, there was one fail; it was so fast, I could not even see what it was. 

I do however at the grub selection have a chance to type in a command, I just don't know what to type and I don't even  know if it will help me here.

Thanks, and if you need any more information, please let me know,

Geoff.

P.s.

My two ATI cards are there just to give me some better options for when I game. In Windows Vista and XP MCE 2005, I have Crossfire setup by way of the CCC (Catalyst Control Center). I can always remove the second card unitl I can get everything right. (I did try all monitor inputs once I noticed that the screen refreshed, but still none had ubuntu on them).

---

### Post by Paul S on 2007-07-29
OK, then I still think there's nothing that will help except fixing your xorg.conf file.

I do believe the "edgy" version of ubuntu should boot on your ATI card, and will automagically configure an xorg.conf with the "vesa" driver.  This is usable until you can get the ATI fglrx driver installed later.

So, you may want to get "edgy" live cd and boot it.  If I'm correct, you should be able to follow my advice and 1) install edgy 2) upgrade to feisty 3) install the ATI fglrx from ATI.

The reason "edgy" will work, but not "feisty" is because of a bug in xorg-7.2.  This bug is in ubuntu, but also in fedora 7 and other distributions that use that version.  So, you won't benefit by switching to another linux.

Too bad you didn't buy nvidia cards, because nvidia supports linux and work out of the box.  But, I understand ATI are a bit better on windows.

HTH,

---

### Post by supersnake83 on 2007-07-31
Paul S,

Thanks for your help, but after trying to install 6.10 it did the same thing; after the selection of the ubuntu install (even if I selected the safe graphic mode) the video is still not supported. 

I did change the vga to 600x800 and still got the same results. I don't have onboard video, so I will be stuck unless I can find a way to make it work.

If you or anyone else can help, thanks; and thanks for your trying and suggestion.

Geoff.

---

### Post by Paul S on 2007-08-01
As I said, the edgy livecd worked on my single ATI card.  The fact that it did not on yours makes me suspect it is because you have 2 ATI video cards.  But, we have to have your /etc/X11/xorg.conf and /var/log/Xorg.0.log files to figure it out.  My suspician is that Xorg is trying to configure xinerama (dual monitors) with a vesa driver and that vesa can't support xinerama.  The Xorg.0.log will show this.  The way to fix it will be to edit xorg.conf and comment out the second video card and xinerama.

Here's an xorg.conf file that works on my single ATI video card.  It uses the "vesa" driver:

```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "Screen0" 0 0
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Synaptics" "CorePointer"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Synaptics"
        Driver      "synaptics"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "auto-dev"
        Option      "Emulate3Buttons" "yes"
EndSection

Section "Device"
        Identifier  "Videocard0"
        Driver      "vesa"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
        EndSubSection
EndSection

```

Your xorg.conf probably has two Device sections and two Screen sections and xinerama in the server layout.  My idea would be to remove one of each, possibly just by removing the xinerama from the server layout.  We'll have to see it to know.  Then once up and running, it would be possible to install the ATI fglrx driver, which supports "big desktop", which is similar to xinerama.

It's also possible that if you create an xorg.conf file from my version (above) and paste it over the existing /etc/X11/xorg.conf, it might work.

If you want to spend the time, another possible approach is to try KNOPPIX, which is a livecd that usually works on most configurations.  Here's the link:

[http://knopper.net/knoppix-mirrors/index-en.html](http://knopper.net/knoppix-mirrors/index-en.html)

Download it, burn it, and try to boot.  If it boots into a graphic mode, then you can use it to mount your ubuntu partition.  Then you can copy these two files and post them in this forum.

If KNOPPIX does not boot into graphics mode, another possibility is MEPIS.  It can be downloaded from:

[http://www.mepis.org/mirrors](http://www.mepis.org/mirrors)

There also is one linux that includes ATI drivers, so it may work.  It's called Sabayon linux.  I have never tried it, so cannot recommend or not recommend it.  But, it might be what you need for your advanced computer.  [http://www.sabayonlinux.org](http://www.sabayonlinux.org)

If none of this works, then it may be necessary to remove one of the video cards for the installation and go through the installation.

You can get familiar with how to do things in linux from here: [https://help.ubuntu.com/](https://help.ubuntu.com/)

In particular read about using the command line starting here:

[https://help.ubuntu.com/7.04/basic-commands/C/](https://help.ubuntu.com/7.04/basic-commands/C/)

HTH

---

### Post by supersnake83 on 2007-08-05
Paul S,

Thanks for that last post&#351; you mentioned how Ubuntu was probably trying to use dual monitors and it then hit me, that Ubuntu is trying to use both of the connectors of my graphics card. So what I did was, I plugged in my VGA (since I was just using the DVI) and that is when the livecd booted. So I then tried Ubuntu that I had installed using the text version and it booted.

Now I am in Ubuntu, (I am actually typing this reply in Ubuntu), I don&#355;t know what to do. You mention my xorg.conf file, I tried typing in that command in the terminal and nothing happened.

If you can, can you let me know how to get those scrips that you asked for, and how to update my graphics driver, so when I put back in my second graphics card (oh, I forgot to mention that I took the second one out) I can still boot to Ubuntu. I also need help changing my resolution, because the default looks a little blurry (well just not sharp and crisp) and small.

Thanks for your time,

Geoff.

p.s.

When grub loads, I have three options for Ubuntu, the top two I can&#355;t remember, but one is listed with &#354;recovery&#354; at the end and the very bottom (even under my Windows loader selection) is Ubuntu 7.04.

Also, is there a way to change my default loader, because I would like the windows loader to be first and the Ubuntu to be second.

Which one should I boot into?

---

### Post by Paul S on 2007-08-06
> **supersnake83 said:**
> Now I am in Ubuntu, (I am actually typing this reply in Ubuntu), I don&#355;t know what to do. You mention my xorg.conf file, I tried typing in that command in the terminal and nothing happened.

That's terrific.  Since you don't know anything about ubuntu or linux yet, then I suggest you take the time to read the documentation and become familiar with the file system, editing files, using the command line, and installing software before you make any changes to your configuration.  Please start with the Documentation [https://help.ubuntu.com/](https://help.ubuntu.com/).

> If you can, can you let me know how to get those scrips that you asked for, and how to update my graphics driver, so when I put back in my second graphics card (oh, I forgot to mention that I took the second one out) I can still boot to Ubuntu. I also need help changing my resolution, because the default looks a little blurry (well just not sharp and crisp) and small.

Most likely the default graphics driver is the "vesa", and it cannot be improved.  It's just a poor substitute for the proprietary ATI binary.  Once you get a bit familiar with ubuntu and linux, you should install the "fglrx" binary.  The wiki has a good explanation of the procedure.  [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)  But, please be sure you know what you are doing before issuing the commands:

```
<<<<< excerpt from BinaryDriverHowto/ATI for feisty >>>>>>

* Install linux-restricted-modules and restricted-manager provied in the restricted repositories:

sudo apt-get update 
sudo apt-get install linux-restricted-modules-generic restricted-manager

Open the restricted drivers manager included in 7.04 "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver". This will hopefully enable fglrx in a painless way.


```
After installing the feisty version of fglrx, you may have to reboot to get the video to load properly.  The resolution should improve, and you should be able to use the configuration tools in gnome to change the resolution, if it doesn't.

This driver gets updated monthly from AMD/ATI and therefore, the version from feisty is a bit outdated.  Using the feisty version should improve your video while you just have one video card installed, but may not be good enough for the dual card, multi monitor setup you use in windows.  So, after you are familiar with how to do things in linux, you will want to get the latest from ATI and install it.

```
<<<<< excerpt from BinaryDriverHowto/ATI for feisty >>>>>>

Install from ati.com (latest version of drivers)
Instructions for 7.04 (Feisty)
Preparation

Although it is possible to use the instructions for 6.10 on 7.04, there is a simpler and possibly more painless way to install of 7.04. First, download the drivers installer (not the rpms) from [WWW] ati.amd.com. It is recommended to save it to an empty directory since the installer will create a bunch of files. Next, in order to build the packages, we need some basic developer tools. To get these tools, first enable the universe and restricted sections of Ubuntu (see AddingRepositoriesHowto for help). Once the repositories are enabled, install the needed developer tools with sudo apt-get install module-assistant build-essential debhelper debconf dh-make fakeroot libstdc++5 linux-headers-generic
Installation

Build Ubuntu packages from the installer by opening a terminal, entering the directory that you saved the installer to, and running bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/feisty

where <version> is the version number of the driver you downloaded. This will take a short time. After finishing, the installer will create several debs. Use the command "dpkg -i <filename>" to install the fglrx-kernel-source<something>.deb and the xorg-driver-fglrx<something>.deb. The other two debs created will be fglrx development headers which you probably will not need and the AMD Control Panel which doesn't work.

After installing the kernel source and xorg driver, you will now need to compile the fglrx kernel module in order to get 3-d rendering. Do so with the following commands:

sudo m-a prepare,update 
sudo m-a build,install fglrx-kernel (or module-assistant -f to force a rebuild if needed)
sudo depmod
sudo rm -f /usr/src/fglrx-kernel*.deb

Configuration

Ubuntu 7.04 ships with a utility to automate configuration of fglrx. Open it at "System -> Administration -> Restricted Drivers Manager" (you may have to install the restricted-manager and linux-restricted-modules-generic package). Select "ATI accelerated graphics driver" and hit apply. The Restricted Drivers Manager will then automagically change xorg.conf and several other files. However, even at this point, the setup is not finished. At next boot, Ubuntu will load an old version of fglrx, so you have to blacklist it by changing /etc/default/linux-restricted-modules-common to include DISABLED_MODULES="somemodule2 fglrx" where somemodule2 is the old contents of that line. When you have finished this last change, reboot and (hopefully) enjoy your 3-d acceleration.
After kernel updates

After every update of the kernel (linux-image-<arch>), you will need to recompile the kernel module (make sure to get the latest linux-headers too) as explained under the installation section. After you recompile the module, you can regain direct rendering by logging into a console (ctrl+alt+f1) and typing:

sudo /etc/init.d/gdm stop (kdm if you use Kubuntu)
sudo rmmod fglrx (even if this command fails, go on)
sudo modprobe fglrx
sudo /etc/init.d/gdm start (again, Kubuntu users type kdm)


```

After installing the latest ATI driver and getting it configured, then you can reinstall your second video card and try rebooting.  There is a Catalyst Control Center in the ATI driver that may help in configuring your xorg.conf to handle the multi card setup you have.  Hopefully it will be similar to the windows CCC.  Since I don't have dual video cards, I can't say for sure how to do this.  But, if you post back with details of error messages, I and others, can help troubleshoot.  And, if you don't get an answer here, pasting an error message into a google search bar will always come up with something.

And, there is a ATI (unofficial) wiki [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) and  [http://rage3d.com/board/forumdisplay.php?f=88](http://rage3d.com/board/forumdisplay.php?f=88)
 and good support lists on phoronix [http://www.phoronix.com/forums/](http://www.phoronix.com/forums/) 

> 
When grub loads, I have three options for Ubuntu, the top two I can&#355;t remember, but one is listed with &#354;recovery&#354; at the end and the very bottom (even under my Windows loader selection) is Ubuntu 7.04.

Also, is there a way to change my default loader, because I would like the windows loader to be first and the Ubuntu to be second.

Which one should I boot into?

Yes, you should boot into the first one, which is the default hilighted entry for ubuntu.  The recovery selection (second line on grub menu) is for fixing it if it won't boot for some reason.  The third is for doing a test of your memory.  You can change the order and the default highlighted line by editing the file /boot/grub/menu.lst.  You'll need to learn how to edit files and do administrative tasks before taking this on.

BTW, once you get this system configured, make sure you make and keep a backup copy of the /etc/X11/xorg.conf file, for use in the future.  Through this experience, you will  become an expert and will be needed to help others on this and phoronix linux forums.  Welcome to linux!

regards,

---

