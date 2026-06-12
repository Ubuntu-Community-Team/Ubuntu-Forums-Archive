---
title: "Old laptop - no graphics"
date: 2008-03-03
forum: General Help
---

### Post by JFASI on 2008-03-03
I have recently tried to set up an old laptop for a friend. This thing has 256mb RAM, and a Pentium III processor. I can't realy tell you more than that, because I can't get any information out of it as it is. I had to install Ubuntu 7.10 from the Alternate install disk because I could not get a GUI running in either normal or safe graphics mode on the LiveCD. Once I installed it off of the disk, I get the same problem: no GUI. 

The install is solid, as it boots into recovery mode perfectly. Judging by the lack of video in both the liveCD and the alternate install, it seems there is no adequate driver for the graphics card (or integrated card, whatever the case may me). Is there any way that I can get this system to live again? It ran perfectly on an install of Ubuntu 5.03 (or something like that, I know it was version 5). 

Thanks for the help.

---

### Post by soldats on 2008-03-03
It may be possible to reinstall 5.1 or whatever version it was then do a few upgrades to the newest version. Also, when you did the alternate install did you do a full desktop version or a cli install. if you did a cli install you'd need the xserver-xorg and a desktop.

---

### Post by Shaythong on 2008-03-03
What kind of Graphics driver is within that old laptop? Since you said you couldn't tell much more than what you've said, that's ok. ;)

---

### Post by jimrz on 2008-03-03
what graphics card is in the laptop?
to find out type
```
lspci
``` from your cli and post the card listed here, so that others with experience of the card may be able to assist.

---

### Post by kerry_s on 2008-03-03
256ram, it's going to slow. try debian instead->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso)

---

### Post by JFASI on 2008-03-04
I suppose I could try installing Xubuntu. I don't think I used the CLI install, but there was no graphical user interface, just an old-timey ASCII screen. 

Also, I ran lspci and got "S3 Inc....Savage" as my VGA compatible controller, and everything else seems to be Intel, from the host controller to the ethernet. 

When I shut it down from recovery mode, it says GNOME desktop manager shutting down. The black screen could be the driver? 

As for installing 5 and upgrading, the machine does not get internet, either through ethernet or wireless, so apt-get upgrade is useless. 

Speaking of which, the ethernet problem seems to still be there, because when I hit :

sudo apt-get install xorg

it just gave me the standard 0 packages response. 

Any ideas?

---

### Post by K.Mandla on 2008-03-04
xorg is probably already installed if you did a full installation; hence when you ask it to install it tells you nothing was done.

If you edit /etc/X11/xorg.conf and set the driver line to savage, it might work. Look for something like this, and change it so it uses the savage driver.
```
Driver "savage"
```
You could also change that line to vesa, but it's probably already tried that.

As for Internet, you can check if it's working with this command.
```
ping www.google.com
```
That just sends out a beep to the Google servers, and if your line is working, Google send a beep back. If not, you have more problems to solve. :roll:

---

### Post by JFASI on 2008-03-04
Ok, so I tried changing the drivers, and it seems to not be helping. Is there any way I could boot the system in verbose mode instead of that Ubuntu splash screen? When I boot it into recovery mode, everything seems to be fine, and there are even some indications that GNOME is running, despite the lack of a GUI. All I get, however, is a blank screen...

If all else fails, I will try to download and install older and older Ubuntu disks until I get graphics.

---

### Post by plucky on 2008-03-04
> Is there any way I could boot the system in verbose mode instead of that Ubuntu splash screen?

At bootup time press <Esc> to enter the Grub menu.Select the Kernel line using up down arrows and then press e To edit the line.Remove **splash** and **quiet** in that line.press <Esc> to exit and enter to continue the bootsequence.

It should now be in verbose mode and you should see lots of text scrolling across the screen.


This is only good for this boot as the edit is only temporary for the one boot.To make it permanent you have to edit the **/boot/grub/menu.lst** file.


Good luck

---

### Post by JFASI on 2008-03-04
Aaaah.. I've been looing for his for a long time. Is there any way I can dump this into a file or something? I obviously can't do this through redirection, since the OS isn't yet loaded. Is there a log file that holds the details of the last boot or something? 

Also, it asks for Ubuntu login, and then roll on regardless. It seems to load GNOME without errors, and even executes boot scripts. Then it attempts to go into GUI mode and fails.

---

### Post by plucky on 2008-03-04
> Then it attempts to go into GUI mode and fails. 

Where does it leave you? 
Does it give you a terminal login prompt? 
Can you configure xorg.conf file?

> Is there a log file that holds the details of the last boot or something?

**Yes** but you need to be logged in on a terminal and type **dmesg** will display the system boot messages.


Good luck

---

### Post by JFASI on 2008-03-04
It leaves me at a blank screen with no cursor. I do see a terminal login prompt, but after a while the boot continues, whether I try to login or not. When I do log in, it gives me a shell and everything, but the boot cascades too quickly to do anything. Im sure I would be able to edit xorg.conf if I had a little more time.

---

### Post by K.Mandla on 2008-03-05
You can pipe the output of dmesg into a text file like this:
```
dmesg > dmesg.txt
```
Be forewarned that if you enter that command more than once, it will overwrite the old file.

---

### Post by JFASI on 2008-03-05
I'll try installing Xubuntu tonight and see what happens. If that fails, I'll reinstall Ubuntu and work from there.

---

### Post by JFASI on 2008-03-06
Ok, so I installed Xubuntu, and it works perfectly. If I were to install Ubuntu through 

sudo apt-get install ubuntu-desktop

and select it through the session manager, do you suppose it would work?

---

