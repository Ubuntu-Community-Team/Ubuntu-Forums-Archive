---
title: "Drivers for nVidia 9500GT"
date: 2014-04-04
forum: General Help
---

### Post by Dobroslav on 2014-04-04
Here are the specs:
ASUS P4V800D-X
Intel Pentium 4 HT 2.80GHz
2.5GB RAM
40GB HDD
nVidia 9500GT

I'm forced to install nVidia proprietary drivers, because everything is slowed down without them - I had same problem on Windows, and I solved it when I installed drivers. Also, I can't set proper screen resolution (mine is 1440x900, and the maximum I can set is 800x600).

I tried almost all versions of this driver (304, 304-update, 319, 334 etc.), and I get the same problem: boot screen changes (it looks like [this]("http://linoob.com/wp-content/flagallery/lubuntu-11-04/02lubuntu-bootsplash.png") when I install drivers), and after few seconds I just get black screen with flashing underscore on the upper left side of the screen. 

I was searching over the Internet about this problem, and I found some solutions which included reinstallation of them, but unsuccessful. Of course, when I run "sudo apt-get remove --purge nvidia*", everything is going back to normal but slow, as I mentioned before.

Using Ubuntu 14.04

---

### Post by Frogs Hair on 2014-04-04
There are various splash screen fixes for Ubuntu caused by installation of Nvidia proprietary drivers posted on the web. They are not identical so keep track of changes in-case the method  doesn't work. I found a method that works on my desktop, but , some methods didn't work and restoring the default was required before trying something new  

[http://askubuntu.com/questions/362722/how-to-fix-splash-screen-in-all-ubuntu-releases](http://askubuntu.com/questions/362722/how-to-fix-splash-screen-in-all-ubuntu-releases)

---

### Post by Dobroslav on 2014-04-04
> **Frogs Hair said:**
> There are various splash screen fixes for Ubuntu caused by installation of Nvidia proprietary drivers posted on the web. They are not identical so keep track of changes in-case the method  doesn't work. I found a method that works on my desktop, but , some methods didn't work and restoring the default was required before trying something new  

[http://askubuntu.com/questions/362722/how-to-fix-splash-screen-in-all-ubuntu-releases](http://askubuntu.com/questions/362722/how-to-fix-splash-screen-in-all-ubuntu-releases)

Thanks for it, but the main problem is that I can't boot into the desktop when I install proprietary drivers.
I'm now writing from Lubuntu without them, everything works okay but screen resolution is low and computer is running slow in general...

---

### Post by Frogs Hair on 2014-04-04
Lubuntu has limited compositing so installing a 3D driver may be part of the problem. I have seen various posts on enabling compositing in Lubuntu so that may be worth looking into . 

[http://askubuntu.com/questions/53745/compositing-in-lubuntu](http://askubuntu.com/questions/53745/compositing-in-lubuntu)

---

### Post by Dobroslav on 2014-04-04
I've installed xcompmgr but it didn't help me to solve the problem.

---

### Post by oldfred on 2014-04-04
You cannot install or overinstall nVidia drivers, they get mixed up and create massive issues.
You have to absolutely purge all old nVidia drivers.


I have a nVidia 9600GT and just install the newest version offered by system settings and it works.
Just did it again with a test install of 14.04, installed nVidia's latests and logged out & back in and it worked great.

 sudo find / -name "nvidia*"
sudo apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

### Post by Dobroslav on 2014-04-05
@oldfred
Doesn't work. After every installation of nvidia drivers I would purge nvidia drivers.

I've now tried to make drivers working with Ubuntu 13.04 (I don't have an empty DVD disc or usb flash memory at the moment so I can't install new version). Everything is too slow because CPU is overloaded, and that's because Nouveau drivers are crap. When I switch to Nvidia proprietary drivers (tested), I get black screen with flashing underscore and I can't access terminal with Ctrl+Alt+F(1-7), so I have to boot into recovery mode.

Any suggestions?

---

### Post by oldfred on 2014-04-05
The minute I get a black underscore I know I forgot nomodeset. I just installed a test 14.04 and on first boot forgot the nomodeset and had the black screen.
But once I install nVidia drivers I have no issues. With my latest install, I did not even reboot, just logged out and back in.

Do not use 13.04 as the repositories are closed, so updates will not work.
       EOL Notice: Raring (13.04) will be End of Life on January 27, 2014
[http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)

---

### Post by edcompsci on 2014-04-06
I don't remember exactly, but I have notes of using this to make mine work way back when.

```

run all commands below as sudo:

edit /etc/default/grub and change the line

GRUB_CMDLINE_LINUX_DEFAULT="nouveau.blacklist=1 quiet splash"

update-grub2

reboot


accept low graphics mode

install nvidia drivers as you normally would

nvidia-xconfig

alt-ctrl-Print_Scrn+k
 or reboot to restart X

to see if nvidia is working: 

inxi -xG

or go to the Nvidia X Server Settings.

```

---

### Post by Dobroslav on 2014-04-18
Hello guys, I was out for a week so I was not able to resolve this problem.

Anyway, I've edited the thread because I have the same problem with (up to date) Ubuntu 14.04. I tried all your solutions but none of them works for me.

Can motherboard cause problem like this? Mine is too old and I suspect that it may be the reason why is this happening..

Regards

---

### Post by Dobroslav on 2014-04-19
I've finally solved my problem! For people who have the same problem like I had, here is the solution:

*I recommend to make a fresh install of your system, if you already have an issue with drivers.*

1. Boot up Ubuntu and make sure you're connected on the internet.
2. Open a terminal with Ctrl + Alt + F1
3. Login and here is what you have to type in terminal:

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install build-essential
sudo apt-get install linux-source
sudo apt-get install linux-headers-generic
sudo apt-get dist-upgrade
sudo reboot
```

4. After reboot, repeat step 2. You'll need here an internet connection, again. Run these commands:

```
sudo apt-get install nvidia-current-updates
**sudo nvidia-xconfig**
sudo reboot
```

**[SIZE=4]It is very important to run nvidia-xconfig! If you don't run it, you'll crash your system![/SIZE]**

After you've done this, you'll have a working nVidia graphics driver. Cheers!

---

