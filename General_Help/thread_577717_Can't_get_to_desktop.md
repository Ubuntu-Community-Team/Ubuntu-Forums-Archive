---
title: "Can't get to desktop"
date: 2007-10-16
forum: General Help
---

### Post by GlennW on 2007-10-16
I know just enough about Ubuntu to be dangerous and that's just what happened!! I made so lame attempt to update using synaptic but inadvertently removed some drivers/packages for my nvidia card. Now I can't get back to the desktop. When I boot up (have dual boot with xp) I end up having to go through the reconfigure process, trying to simplify things so that it will at least get me back to the desktop so that I can reload the requisite packages.

Anyway, after the reconfig process, I end up back at root@glenn-desktop:~#

Can anyone give me some advice as to how to proceed from here? 

Do I need to resolve this issue or install 7.10 over it? (I really don't know what that means) Will installing 7.10 overwrite 7.04 despite it being broken?

Anxious fan...........

---

### Post by santiagoward2000 on 2007-10-16
Hi GlennW,
Once you enter Ubuntu, you get a console screen? Have you tried using apt-get to install the drivers you removed?
Just try:
```
sudo apt-get install nvidia-glx
```

I hope this helps!

---

### Post by GlennW on 2007-10-16
Hi santiagoward2000,

Thanks for the suggestion. I tried it at the console, to no avail. I also ran

[INDENT]sudo dpkg-reconfigure xserver-xorg[/INDENT]

to reduce everything to its most simple settings. But still I just end up back at the console. I don't understand the lines before 

[INDENT]glenn@glenn-desktop~$[/INDENT]

I am quite puzzled. I am looking forward to 7.10 but, again, can I install "over" 7.04 or do I have to uninstall 7.04 first? In which case, how do I access it to uninstall it?

Thanks for any help.....

---

### Post by santiagoward2000 on 2007-10-17
> **GlennW said:**
> Hi santiagoward2000,

Thanks for the suggestion. I tried it at the console, to no avail. I also ran

[INDENT]sudo dpkg-reconfigure xserver-xorg[/INDENT]

to reduce everything to its most simple settings. But still I just end up back at the console. I don't understand the lines before 

[INDENT]glenn@glenn-desktop~$[/INDENT]

I am quite puzzled. I am looking forward to 7.10 but, again, can I install "over" 7.04 or do I have to uninstall 7.04 first? In which case, how do I access it to uninstall it?

Thanks for any help.....

If that didn't worked,I don't know how to fix it. But if you want to reinstall it, all you need to do is use the Ubuntu CD, delete it's partition and install all over. Perhaps if you use a LiveCD you could access your partition and backup your data.

---

### Post by GlennW on 2007-10-17
> **santiagoward2000 said:**
> ...But if you want to reinstall it, all you need to do is use the Ubuntu CD, delete it's partition and install all over. Perhaps if you use a LiveCD you could access your partition and backup your data.

The only CD I have is the one I used for the original install. I've tried recently to boot from it but without success. What's a LiveCD?

---

### Post by anaconda on 2007-10-17
I always solve those problems by typing:
```
nano /etx/X11/xorg.conf
```
and search for a place like:

Section "Device"
    Identifier     "Videocard"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"

And change the Driver to "nv" instead of "nvidia"
This will change the nvidia driver to be the free opensource nv driver, which works with all nvidia cards, but wont have 3d acceleration or direct rendering.

Dont know how the nv driver works with desktop effects if you have those enabled.

---

### Post by santiagoward2000 on 2007-10-17
> **GlennW said:**
> The only CD I have is the one I used for the original install. I've tried recently to boot from it but without success. What's a LiveCD?

Hmmm, a LiveCD is the one that is normally used to install. Before you installed it, could you use the system? If so, then it's a LiveCD. The other option is the AlternateCD, which lets you install the system from a command line.
You said you had no success booting from the CD. Do you get any error message?

---

### Post by GlennW on 2007-10-17
> **anaconda said:**
> I always solve those problems by typing:
```
nano /etx/X11/xorg.conf
```
and search for a place like:

Section "Device"
    Identifier     "Videocard"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"

And change the Driver to "nv" instead of "nvidia"
This will change the nvidia driver to be the free opensource nv driver, which works with all nvidia cards, but wont have 3d acceleration or direct rendering.


Thanks anaconda, I did get further with your advice although I didn't have permission to save the adjusted xorg.conf. So, back to "sudo dpkg-reconfigure xserver-xorg" and at least I could get it to the point now where X actually loads but the screen is really bad artifacts (bars and blocks). Screen is fine when booting back to xp so means the video card is fine.

At one point, though, prior to using your advice, I tried "startx" and came up with this stuff (more or less)

[INDENT]Using config file: "/etc/X11/xorg.conf"[/INDENT]
[INDENT]Error: API mismatch: the NVIDIA kernel module has version 1.0-9755, but this X module has version 1.0-9631. Please make sure that the kernel module and all NVIDIA components have the same version.[/INDENT]

So this is where I am. I have no idea where to go at this point. Can I just wait for tomorrow, download 7.10 and do a fresh install? How do I uninstall 7.04?

Oops! This might help.

Dual boot - 7.04 and xp
P4 1.6 GHz
512 MB RAM
80 GB HD
nVidia Geforce 6200 256 MB DDR2 TV DVI
Samsung SyncMaster 205bw
Broken Ubuntu 7.04

---

