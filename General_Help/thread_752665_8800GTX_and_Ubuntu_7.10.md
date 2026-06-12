---
title: "8800GTX and Ubuntu 7.10"
date: 2008-04-11
forum: General Help
---

### Post by Eclyps19 on 2008-04-11
I'm having trouble doing an install from the CD. I am going to guess it's because of the 8800GTX. I get to the kernel loading part (right after you go the install screen). Then it just sits there. I let it go for about 20 mins and nothing.

My other hardware

q6600 @ 3.0
8800GTX
2GB DDR2 800
160GB IDE
250GB SATA (Want linux on here)
350GB SATA (Windows Vista on here)

Suggestions?

---

### Post by tvtech on 2008-04-11
have you done a data integrety check on the cd?  have you tried to start it in safe graphics mode?  have you for the fun of it pulled the windows disk and seen if it can boot without it in there. ?

---

### Post by Eclyps19 on 2008-04-11
actually I can't even check the integrity of the CD. does the same thing. Says loading the kernel and then black screen :(

I can boot into windows just fine

---

### Post by Gauvenator on 2008-04-11
You need to boot off the CD into a terminal.  Then:

```
nano /etc/X11/xorg.conf
```

Change in the Device section the driver to "vesa"

Then you should be able to start the user interface by typing exit.

---

### Post by Eclyps19 on 2008-04-11
sorry, I'm still a bit of a linux noob.

How do I get into the terminal from the cd?

and then when I get in that config I find devices and change it to vesa?

---

### Post by Gauvenator on 2008-04-11
> **Eclyps19 said:**
> sorry, I'm still a bit of a linux noob.

How do I get into the terminal from the cd?

and then when I get in that config I find devices and change it to vesa?

To get into a terminal, I believe in the live CD when you select the option to start or install ubuntu you can edit it's flags.  Delete the last one "quiet splash--"  if I remember correctly.

In the file, there will be a section called "device"
In that section, there will be a line starting with driver, and in the text after it, change the thing in parentheses to "vesa"

For example:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
```
You would change "nvidia" to "vesa"

---

### Post by Eclyps19 on 2008-04-11
actually, all i did was remove the quiet splash and it started working fine.

appreciate it :)

---

### Post by Gauvenator on 2008-04-11
> **Eclyps19 said:**
> actually, all i did was remove the quiet splash and it started working fine.

appreciate it :)

You're welcome. Glad it worked out.

---

### Post by Eclyps19 on 2008-04-11
argh... so it installed just fine. upon reboot, getting the same thing. I can get to the recovery console, but i might as well just boot into windows and edit any configs?

should I edit /etc/X11/xorg.conf with the above driver change?

---

### Post by Gauvenator on 2008-04-11
> **Eclyps19 said:**
> argh... so it installed just fine. upon reboot, getting the same thing. I can get to the recovery console, but i might as well just boot into windows and edit any configs?

should I edit /etc/X11/xorg.conf with the above driver change?

Yes I would edit the xorg.conf so you can boot and install the latest nVidia drivers ASAP.

Use Envy to make it easy.
[http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb)
Download that and then install it.  You should be able to just double click it.

---

### Post by Eclyps19 on 2008-04-11
hmmm... for some reason I can't see the drive I installed linux on in windows. I can find it in the disk manager, but it doesn't show a file system next to it and it's broken in 2 pieces. One at 5GB and the rest of the disk in the other part.

Does ubuntu default to ntfs or a different system?

---

### Post by Gauvenator on 2008-04-11
> **Eclyps19 said:**
> hmmm... for some reason I can't see the drive I installed linux on in windows. I can find it in the disk manager, but it doesn't show a file system next to it and it's broken in 2 pieces. One at 5GB and the rest of the disk in the other part.

Does ubuntu default to ntfs or a different system?

Ubuntut uses ext3, which Windows can't read.  You should just dl Envy when ur in Ubuntu, it's not very big.

The 5gb is probably the swap partition, and the rest is your root.

---

### Post by Eclyps19 on 2008-04-11
got it. thanks.

in ubuntu now. gunna try to get those drivers now. 

again, thanks for all the help

---

### Post by Eclyps19 on 2008-04-11
well, installed the drivers with envy, but upon reboot it's a blank screen again. Change it back to vesa?

---

### Post by Gauvenator on 2008-04-11
Change it to vesa so you can get into ubuntu, then run:

```
sudo nvidia-xconfig
```

Then reboot.

---

### Post by Eclyps19 on 2008-04-11
mm sweet. xorg.conf is empty now.

=\

now what?

---

### Post by Eclyps19 on 2008-04-11
ahh nvm. didn't know case mattered :(

---

### Post by Eclyps19 on 2008-04-11
alright. ran what you told me to. it told me it backed up the conf and then wrote to it. I rebooted and I'm getting the black screen again.

Any other ideas?

---

### Post by PmDematagoda on 2008-04-11
Boot Ubuntu in Recovery Mode and then execute:-
```
sudo dpkg-reconfigure xserver-xorg
```
and select the driver as "nvidia" and any other options you may want and then start the X-Server with:-
```
startx
```
If that works then reboot and see if the X-Server works in normal mode.

---

### Post by Eclyps19 on 2008-04-11
> **PmDematagoda said:**
> Boot Ubuntu in Recovery Mode and then execute:-
```
sudo dpkg-reconfigure xserver-xorg
```
and select the driver as "nvidia" and any other options you may want and then start the X-Server with:-
```
startx
```
If that works then reboot and see if the X-Server works in normal mode.
well, I successfully got into x-server, but upon reboot I got the black screen again.

---

### Post by Eclyps19 on 2008-04-11
well, can i log in from the recovery console to at least give me full access when I run startx?

---

### Post by Eclyps19 on 2008-04-12
sounds like a lot of ppl are having more success with the 32 bit version... should I download that and give it a try with a fresh install?

---

### Post by Gauvenator on 2008-04-12
> **Eclyps19 said:**
> sounds like a lot of ppl are having more success with the 32 bit version... should I download that and give it a try with a fresh install?

Sure, give it a try.  But you probably will still have some shenanigans with your 8800 and the live CD.  I was able to get Mint (32bit, ubuntu based) working with my 8800gt.

---

### Post by Eclyps19 on 2008-04-12
so is this an issue with nvidia or an issue with ubuntu? I'd really like to get my 8800GTX working on 64 bit, but everything I've tried just flat out fails. Could it be trying to load a res that my monitor can't handle? I can tell some process is running in the background, and my monitor doesn't turn off, just black.

Any way to force a resolution before it loads the gui?

---

### Post by PmDematagoda on 2008-04-12
> **Eclyps19 said:**
> well, can i log in from the recovery console to at least give me full access when I run startx?
You don't usually login to the recovery console unless you have assigned a password to the root account, so you should be able to just execute startx.

---

### Post by Eclyps19 on 2008-04-12
How can I force a startup resolution of 1680x1050?

It seems to work perfectly if I type startx, but I don't log in or anything so I don't have access to the internet. I'm just a privileged user (I think that's what it tells me).

---

### Post by PmDematagoda on 2008-04-12
You can force the resolution by specifying it in the X-Server reconfiguration.

Did you reboot the PC and check if the X-Server still works?

---

### Post by Eclyps19 on 2008-04-12
> **PmDematagoda said:**
> You can force the resolution by specifying it in the X-Server reconfiguration.

Did you reboot the PC and check if the X-Server still works?
yup. rebooted several times and x-server worked just fine by typing startx. 

I gave up and I'm currently installing 32 bit. I can live without 64 bit, and the 32 bit got to the gui install screen without and command line changes (and at the proper res) so I'm assuming this one will work. Hopefully the 64 bit drivers for the 8800s will be fixed soon.

Thanks everyone for the help. I'll probably be on here in another hour freaking out again :)

---

