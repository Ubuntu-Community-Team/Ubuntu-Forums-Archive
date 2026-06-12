---
title: "Mouse cursor not moving in 16.10 live session"
date: 2016-10-13
forum: General Help
---

### Post by jaarvidsen on 2016-10-13
Hi

I was just booting the brand new 16.10 ubuntu gnome from usb stick. The problem is that the mouse cursor doesent move, its just stuck in the top left corner. Its just the cursor that is stuck, the mouse 'moves' but i cant see where its moving unless its hovering above a button or something that changes when the mouse is above it.

The mouse is a wireless Logitech G602. I tried with some other logitech wireless mouse as well and the exact same thing happened.

Incidently exactly the same happened when i tried budgie-remix 16.10 beta 2 (i think) a few weeks ago so i suspect it would happen in the ubuntu/unity edition too

This is on a self built desktop computer with an Asus Z170I Pro Gaming with a 6700K processor. everything worked fine in 16.04

I dont know if this will also happen with the fully installed 16.10 system as im reluctant to install it without knowing if the mouse will work.

However booting my laptop which is a slightly older intel based system and using the same mouse the problem does not occur, which makes me think there must be a bug affecting the z170 motherboards?

any help or hint appreciated

thanks

---

### Post by jaarvidsen on 2016-10-14
update: 
just tried booting ubuntu (unity) 16.10 usb live session - same as above. cant move cursor
also booted ubuntu gnome 16.04.1 usb live session - problem does not occur

also tried all of the below which i found somewhere on the net. NONE of it fixes the problem
(the mouse/receiver is recognized by the first command):
-------------------------------------------------------
Check that the mouse was recognized by your computer

    Type Ctrl+Alt+T to open the Terminal.

    In the terminal window, type xsetpointer -l | grep Pointer, exactly as it appears here, and press Enter.

    A short list of mouse devices will appear. Check that at least one of the items says [XExtensionPointer] next to it, and that one of the [XExtensionPointer] items has the name of the mouse to the left of it.

    If there is no entry that has the name of the mouse followed by [XExtensionPointer], then the mouse was not recognized by your computer. If the entry exists, your mouse was recognized by your computer. In this case you should check that the mouse is plugged in and in working condition.
-----
gsettings set org.gnome.settings-daemon.plugins.cursor active false
----
bring the cursor back with Ctrl+Alt+F1 followed by Ctrl+Alt+F7
---
sudo modprobe -r psmouse # disable the driver 
sudo modprobe psmouse # enable the mouse driver
----------------------------------------------------

*sniff*

---

### Post by ikasou on 2016-10-14
> **jaarvidsen said:**
> update: 
just tried booting ubuntu (unity) 16.10 usb live session - same as above. cant move cursor
also booted ubuntu gnome 16.04.1 usb live session - problem does not occur

also tried all of the below which i found somewhere on the net. NONE of it fixes the problem
(the mouse/receiver is recognized by the first command):
-------------------------------------------------------
Check that the mouse was recognized by your computer

    Type Ctrl+Alt+T to open the Terminal.

    In the terminal window, type xsetpointer -l | grep Pointer, exactly as it appears here, and press Enter.

    A short list of mouse devices will appear. Check that at least one of the items says [XExtensionPointer] next to it, and that one of the [XExtensionPointer] items has the name of the mouse to the left of it.

    If there is no entry that has the name of the mouse followed by [XExtensionPointer], then the mouse was not recognized by your computer. If the entry exists, your mouse was recognized by your computer. In this case you should check that the mouse is plugged in and in working condition.
-----
gsettings set org.gnome.settings-daemon.plugins.cursor active false
----
bring the cursor back with Ctrl+Alt+F1 followed by Ctrl+Alt+F7
---
sudo modprobe -r psmouse # disable the driver 
sudo modprobe psmouse # enable the mouse driver
----------------------------------------------------

*sniff*

Facing exactly the same problem with the live 16.10 USB on a X99 system - x99e-itx/ac, GTX 1080. My mouse is a regular USB optical mouse connected via USB 2.0. Recognised properly according to the xsetpointer test above. This is a gui issue, not a hardware issue imho...

---

### Post by jaarvidsen on 2016-10-14
> **ikasou said:**
> Facing exactly the same problem with the live 16.10 USB on a X99 system - x99e-itx/ac, GTX 1080. My mouse is a regular USB optical mouse connected via USB 2.0. Recognised properly according to the xsetpointer test above. This is a gui issue, not a hardware issue imho...

im wondering if it has to do with the nouveau drivers and  gtx 10XX cards, ive got a gtx 1070. ive just tried plugging the monitor into the motherboard/intel socket but i just got no picture which is weird cos it used to work before, maybe its because i upgraded my bios yesterday to see if that would solve any of the problems in my original post(which it didnt) and maybe i forgot to reset some setting in bios, ill have to look into that tomorrow or something

PS glad im not alone cos i cant find any info on this on the net

---

### Post by ikasou on 2016-10-14
Was thinking the same .. will try and lookup some boot flag to disable them and use legacy vga as a test

---

### Post by mh2721 on 2016-10-14
I had this same problem in beta.  And now in release 16.10,  I found for me it's the 4.8 kernel, because I installed 4.7.7 in 16.10 and the mouse works fine.  
If I install 4.8 in another distro, same problems with mouse.

My computer:  Gigabyte Z170x-gaming-5 (there is no IOMMU option in bios to try),  Nvidia 1070.

---

### Post by ikasou on 2016-10-16
Is definitely the video driver i think, just apt-get install nvidia-370 from phoronix's ppa-drivers and issue gone for me (always on the stock 4.8.22 kernel that comes with Ubuntu 16.10)

---

### Post by jaarvidsen on 2016-10-21
i managed to install using just keyboard, then installed the 370 drivers from the ppa and now it simply wont boot properly, it gets stuck halfway with some text saying 'sda1 is clean blabhblah' 
so now im using intel graphics, which actually is smoother than nvidia, much smoother really. only problem is i gotta switch the cable back to the nvidia card whenever im booting windows to play a game. 

wonder how it would work if i plugged a second cable into the monitor one with intel graphics and one with nvidia

---

### Post by fendry on 2016-12-06
I'm having the same issue ! 

I tried the the latest driver from the PPA but then blocked on the clean sda5... Or on the terminal screen with the nomodeset....

I don't know what to try after that...

---

### Post by aman207 on 2017-01-08
Having the exact same issue as well. Nothing in this thread has made my mouse pointer move. Has anyone found a fix or is this a bug we have to wait to get fixed?

---

### Post by hotrod2 on 2017-02-24
Same issue here, 0 useful troubleshooting suggestions found so far.

I was able to install Ubuntu server and then the nvidia driver and kubuntu-desktop packages but upon reboot I only get the login screen and the cursor turns to an X when I enter my password.

I'm a little shocked there isn't more discussion about this...  I upgraded to my 1070 while I had a working 16.04 install and somehow didn't encounter any issues.  At this point it seems like it's impossible for me to install a fresh copy of Ubuntu / Kubuntu...  Help would be appreciated.

---

### Post by davidmohammed on 2017-02-27
suggestion - do actually install - you can navigate via keyboard cursors and tab key: try the libinput driver instead of the synaptics driver - both control the mouse and touchpad - you should only install one of them.

CTRL+ALT+T to open a command window OR CTRL+ALT+F2 to open the TTY F2 (login)
sudo apt update
sudo apt install xserver-xorg-input-libinput
sudo apt purge xserver-xorg-input-synaptics

then reboot
sudo reboot --

---

### Post by kadiliman on 2017-02-28
Had the same problems, but managed to have a workaround.

I have a clevo p650rs 1070 with 4k

I changed the GPU from discrete to mshybrid

Then at the grub selection I typed e and changed the gfxpayload=keep to gfxpayload=text

That allowed me to boot into the desktop with the mouse cursor behaving properly.

---

