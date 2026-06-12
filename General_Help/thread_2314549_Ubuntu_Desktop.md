---
title: "Ubuntu Desktop?"
date: 2016-02-22
forum: General Help
---

### Post by mark.hilt1 on 2016-02-22
So this is a bit more confusing so sorry if I posted this in the wrong forum area have not used ubuntu forums before now for what I want is to do something like arch linux where you start with a command line (Based on ubuntu) and choose the desktop and everything else I want from the ground up to bare minimal? is this possible or? this is for a personal desktop computer also could I do this with Ubuntu server? or? I am not new to linux ive been using Ubuntu and mint for a few years as well as arch and fedora

Edit: I have installed ubuntu server 14.04 with kubuntu using [FONT=Consolas]sudo apt-get install kubuntu-desktop --no-install-recommends

[/FONT]

---

### Post by HermanAB on 2016-02-22
Well, everything you want to do is possible, but not necessarily easy to achieve.  You will likely end up rebooting umpteen times before you got it all just right.  

You can install multiple desktop systems, but Gnome and KDE typically don't like each other much, since each wants to use its own window manager.  You can also boot into text mode and then start the GUI with the startx command.

So, go ahead, have fun.  You will eventually get it all going.

---

### Post by mark.hilt1 on 2016-02-22
> **HermanAB said:**
> Well, everything you want to do is possible, but not necessarily easy to achieve.  You will likely end up rebooting umpteen times before you got it all just right.  

You can install multiple desktop systems, but Gnome and KDE typically don't like each other much, since each wants to use its own window manager.  You can also boot into text mode and then start the GUI with the startx command.

So, go ahead, have fun.  You will eventually get it all going.
Hello Herman thanks for the reply I ended up installing Kubuntu with Minimal settings on the ubuntu 1404 server and it runs great for now I may in the future switch from KDE to enlightenment 19 though

---

### Post by grahammechanical on 2016-02-22
You want, first of all, some punctuation in your posts. Please.

Next you can try the minimal Ubuntu ISO CD Image. And it is minimal, as it is only a few MB in size. You can start with just Linux installed and then install every other package from the command line. Or select a desktop environment to be part of the installation.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

> To install, boot your computer from the the mini iso  and select "Install" at the prompt.  You can then follow the  instructions from the text-based installer.  On the software selection  screen, you can select from a number of collections of software such as  different desktop environments (kde, xfce, etc), a multitude of  different servers, multimedia creation tools, media center (mythbuntu),  etc.  You can also select "Manual package selection" which will take you  to aptitude.  You may also select nothing and just continue to finish  the installation.  If you selected nothing, upon reboot you will arrive  at a cli prompt; from here you can fully customize your new system. 


**Note:**  While the minimal iso image is handy, it isn't useful for installing on  UEFI-based systems that you want to run in UEFI mode. The mini iso  lacks the proper files for booting the computer in UEFI mode. Thus, the  computer will boot in BIOS compatibility mode, and the installation will  be in BIOS mode.

Regards

---

### Post by Bucky Ball on 2016-02-22
As above. The minimal install will do exactly what you want, but you need to do some research to get it ticking nicely.

During the install you will arrive at a section called 'tasksel'. Don't select a 'machine profile' here. When the install is finished you will have the Ubuntu kernel installed only and the machine will reboot to a large terminal. Login and start installing things with:

```
sudo apt-get update
sudo apt-get install <app_here>
```

... where <app_here> is what you want to install. For instance:

```
sudo apt-get update
sudo apt-get install xfce4 synaptic firefox leafpad thunderbird lightdm --no-install-recommends
```

... will get you a basic, running system on reboot.

Links for the mini install:

Minimal Install page:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Older, but info still relevant while screenshots might be a bit different now:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

First boot basic install from above link:
```
sudo apt-get update
sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic --no-install-recommends
```

A variation on a theme. The research part comes when you write down what you want to install on a piece of paper prior to switching the computer on. It pays to have a plan with a minimal install because you want to get it right and you can accidentally bloat or worse if you start installing things haphazardly. 

Important note: if you do a minimal install then install 'ubuntu-desktop' or any '*buntu-desktop', it defeats the purpose of a minimal install. ubuntu-desktop, for instance, basically gives you a full Ubuntu install. Not much point in taking the trouble to do a mini. :-k 

Good luck. :)

---

### Post by mark.hilt1 on 2016-02-22
> **grahammechanical said:**
> You want, first of all, some punctuation in your posts. Please.

Next you can try the minimal Ubuntu ISO CD Image. And it is minimal, as it is only a few MB in size. You can start with just Linux installed and then install every other package from the command line. Or select a desktop environment to be part of the installation.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)



Regards Thanksss III will do that        looks better then the server iso downloading now

---

