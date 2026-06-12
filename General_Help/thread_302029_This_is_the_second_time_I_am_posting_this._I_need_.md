---
title: "This is the second time I am posting this. I need help compiling the kernel-source."
date: 2006-11-18
forum: General Help
---

### Post by Slyth100 on 2006-11-18
I have waited a week and got no response from when I posted this in Absolute Beginner talk. So, now I am trying this forum in the hope that somebody can help me.

I am currently compiling kernel-source 2.4.27 for Ubuntu for kernel 2.6.15-23-386.

This version of the kernel-source came with a cd package so I hope its the right version...anyway I keep getting this message when I type in 'make dep.' I have already typed in make old config and that worked fine.

Anyway the error message is:

gcc-3.3 -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -o scripts/mkdep scripts/mkdep.c
make: gcc-3.3: Command not found
make: *** [scripts/mkdep] Error 127


I currently have gcc 4.0 installed. But I don't want to install gcc3.3 as this will probably mean reinstalling an earlier version of GCC which could well screw up my system...

ANY help would be greatly appreciated. ](*,)

---

### Post by RFScheer on 2006-11-18
Your question is quite challenging because there are aspects of misunderstanding in it and also it's a really old source your're working with.

If you look at the description of the kernel source, it's not for a modern kernel but for version 2.4.27, a very old one.  

Perhaps you are going in the wrong direction.  What is it you want to accomplish with the new kernel?  There is probably a much easier way than you expect.

Sorry if I'm misunderstanding.

---

### Post by Slyth100 on 2006-11-18
Why would the people who send out the CD packages to people who are setting up Ubuntu for the first time include an old kernel-source???

Anyway, the reason I am trying to compile the kernel source is so I can set up the nvidia drivers on my computer. When I try to set it up it says I need the kernel-source. Unfortunetly, I have to use a friends computer to use the internet as I can't afford a modem. Surely, I am not the only person who uses linux who doesn't easy access to the internet. I love using linux because it is so much faster than windows but I do find it frustrating that so much of it depends on downloading from the internet. That is one of the reasons why I decided to buy a package with 3 cds as I hoped all of the relevant programs would be on there.

---

### Post by RFScheer on 2006-11-18
Ahh, very good.

I'm not sure what's on your cd's but am pretty sure the nvidia driver isn't.  Have you already downloaded it from nvidia somehow?  You will need that but you won't need to recompile your kernel:)

Let me go look around on how to do the nvidia driver install and I'll be right back.

You're on dapper drake, right?

---

### Post by Slyth100 on 2006-11-18
I have downloaded the latest nvidia  drivers and have it sitting on the desktop. I have done some research already and as I understand you have to press Control Alt F1 and then type sudo /etc/init.d/gdm stop in order to stop X so I can install the drivers.

Is  this correct?

---

### Post by Slyth100 on 2006-11-18
I forgot to mention that I am on drapper drake.

---

### Post by RFScheer on 2006-11-18
Ok, right, the easy way to do this definitely involves some internet work.  You would want this package:

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.2-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.7.2-0ubuntu1_all.deb)

But it's going to want to download the nvidia files which are kinda large for a modem connection.  

It's too bad you can't connect your machine to a friend's internet connection for a few hours and you could just run Automatix to set up everything automatically!!

It's been awhile since I've installed the nvidia driver the way you want to.  Let me go check some things about that.

---

### Post by Slyth100 on 2006-11-18
Thanks for sticking with this - I appreciate your help :)

---

### Post by RFScheer on 2006-11-18
Here,s an excerpt from the dapper customization guide for doing offline nvidia install like you (probably still) want to do:)

METHOD 1 - OFFLINE INSTALLATION

1) Install the restricted modules for your kernel:

Type:

```
sudo apt-cdrom add
```

then it should ask you to insert Ubuntu's cd.

Then (after the previous process finishes) type:

```
sudo apt-get update
```

```
sudo apt-get install linux-386
```


2) Download this package from another computer (in which you have an internet connection):

Use this package if you run Ubuntu 32bit:

Nvidia_package_32

OR this package if you run Ubuntu 64bit:

Nvidia_package_64

Then move the package to your computer with Ubuntu (use a USB pen for example): Double click on the .deb file and install it.


3) Backup your xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```


NOTE: if you lost your old xorg.conf or that doesn't work type this:

```
dpkg-reconfigure -phigh xserver-xorg
```


4) Then IF AND ONLY IF the installation of the package went fine, set up your xorg.conf:

```
sudo nano -w /etc/X11/xorg.conf
```


Get to the Section "Module" and put a "#" before load dri and load glcore so that it looks like this:


```

Section "Module" 
   Load "i2c" 
   Load "bitmap" 
   #Load "dri" 
   #Load "glcore" 
   Load "ddc" 
   Load "extmod" 
   Load "freetype" 
   Load "glx" 
   Load "int10" 
   Load "type1" 
   Load "vbe" 
EndSection

```

Then get to the Section device and set the driver to "nvidia" (instead of "nv" or "vesa"):

```
Driver "nvidia"
```


CTRL+X to exit (save the file)

5) Then log out and press CTRL+ALT+Backspace

NOTE: if you need to uninstall the driver you have to read the section "HOW TO UNINSTALL THE DRIVER" which you can find right after Method 1 (the online installation)

---

### Post by RFScheer on 2006-11-18
That excerpt required a bit of re-editing to copy over correctly.  Look at the original if there are any questions.

[http://doc.gwos.org/index.php/DapperCust](http://doc.gwos.org/index.php/DapperCust)

---

### Post by Slyth100 on 2006-11-18
Thanks I will try that right now!!!:D

---

### Post by Slyth100 on 2006-11-18
Thanks I will try that right now!!!

---

### Post by Slyth100 on 2006-11-18
Thanks you so much!!! IT WORKS!!!:-D

---

