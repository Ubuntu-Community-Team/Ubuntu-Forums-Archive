---
title: "Blank screen after installing nvidia drivers on 18.10"
date: 2019-01-20
forum: General Help
---

### Post by Macmee on 2019-01-20
I have an alienware x51 r3. It has a connectorless igpu and a dGPU: PNY Nvidia GTX 970.

I installed and booted Ubuntu 18.10 no problem. I ran **sudo ubuntu-drivers devices** and it detected the 970 no problem. I ran** sudo ubuntu-drivers autoinstall** and then rebooted.

Now I boot up and the screen flashes from the "ubuntu black" color to pure black, back to the "ubuntu black" color where it remains forever. I also cannot get a shell up with ctrl-alt-f1.

Kind of scratching my head here in terms of what to do to fix this. I can boot into the recovery shell from the boot manager just fine but I don't know what to do to keep the drivers and fix the black screen.

---

### Post by CatKiller on 2019-01-21
> **Macmee said:**
> I also cannot get a shell up with ctrl-alt-f1.

Try 2. Recent versions use 1 instead of 7 for the normal display.

---

### Post by Macmee on 2019-01-21
> **CatKiller said:**
> Try 2. Recent versions use 1 instead of 7 for the normal display.

I gave it a shot but nothing happens. I'm not totally sure why because I end up on the black/purple screen after verbose boot finishes so I assume I should be able to get into text mode. Recovery mode works fine though I guess.

I tried a fresh install of 18.10 and am experiencing the same issue. The Nouveau drivers by default seem to work only with DVI though (cant use HDMI) which is a requirement for me since I want dual displays.

Very confused still why I'm getting the black screen with the proprietary drivers. I'm doing autoinstall and can see that it's installing nvidia-390. It should blacklist Nouveau for me from everything I read, but I'm even doing it manually in a modprobe file and still getting the same issue.

At a loss here in terms of what to do.

Nvidia driver:
instant black screen on boot on both DVI and HDMI. The screen isn't off though, it's just black/purple

Nouveau driver:
DVI boot works fine, get to the desktop and everything works. HDMI works up to the ubuntu logo during bootup. I get the correct resolution and also see a cursor but then the screen goes completely off.

edit: HOLY SHOE, the nvidia-driver-390 along with installing lightdm fixed my issue! But I wonder why gdm3 wont work... still trying to figure it out although for now I'm happy to boot back into my desktop.

---

### Post by CatKiller on 2019-01-21
> **Macmee said:**
> But I wonder why gdm3 wont work... still trying to figure it out although for now I'm happy to boot back into my desktop.

As I understand it (I don't use Gnome) GDM defaults to using Wayland if you're using accelerated graphics, but Wayland doesn't work if you're using the Nvidia drivers.

Since almost all of the people using accelerated graphics are going to be using the Nvidia drivers, that seems like a stupid decision to me. It's because of things like that that I don't use Gnome.

Glad you found a solution.

---

### Post by Macmee on 2019-01-26
> **CatKiller said:**
> As I understand it (I don't use Gnome) GDM defaults to using Wayland if you're using accelerated graphics, but Wayland doesn't work if you're using the Nvidia drivers.

Since almost all of the people using accelerated graphics are going to be using the Nvidia drivers, that seems like a stupid decision to me. It's because of things like that that I don't use Gnome.

Glad you found a solution.

what do you use instead of GNOME?

---

### Post by CatKiller on 2019-01-26
> **Macmee said:**
> what do you use instead of GNOME?

My old desktop was using mainly Compiz; essentially Unity without the Unity bits. My laptop uses Cinnamon. My new desktop uses KDE.

They each have their quirks and foibles, but they don't seem deliberately malicious like Gnome has seemed to be over the past few years.

---

### Post by giulio-castelli on 2019-04-19
Dear both,

I get the same problem while installing Ubuntu 19.04 on a brand new ASUS Zenbook.

The problem is that I am almost a total beginner. Can you help me how to solve?

I actually start the pc and see the blank screen afterwards. I cannot open the terminal with Ctrl-Alt-F1.

I am totally confused  :confused::confused::confused:

Best
Giulio

---

### Post by hgkrug1 on 2019-05-23
This is a problem with Ubuntu 19.04 as well.  I have not yet found a solution.  I found 2 ways to restore your Ubuntu desktop - see entry #17 at [https://ubuntuforums.org/showthread.php?t=2411777&page=2](https://ubuntuforums.org/showthread.php?t=2411777&page=2)

---

### Post by mastablasta on 2019-05-23
solution could be to make xorg default before installing drivers.

or simply to use another desktop environment like KDE, Xfce...

---

### Post by hgkrug1 on 2019-05-23
I found a solution for this Nvidia driver issue (on ubuntu 18 and 19). See instructions at the top at [https://ubuntuforums.org/showthread.php?t=2419319&highlight=nvidia+drivers](https://ubuntuforums.org/showthread.php?t=2419319&highlight=nvidia+drivers), it worked for me!

Unfortunately, I could not reproduce the installation on a freshly installed system.

However, I found a suitable fix at entry #19 of [https://bugs.launchpad.net/gdm/+bug/1798790](https://bugs.launchpad.net/gdm/+bug/1798790)

Try this as a workaround: edit /etc/gdm3/custom.conf 
and uncomment the line: 
#WaylandEnable=false

---

### Post by fely35 on 2019-06-25
Ubuntu 19.04, nvidia-418: The solution for me was to set the primary display in the PC BIOS to Auto, instead of Nvidia. The bios mentioned that if NVIDIA is selected, the Intel GPU is also active. If you don't have that bios option: Nvidia Optimus: [https://wiki.archlinux.org/index.php/NVIDIA_Optimus#Display_Managers](https://wiki.archlinux.org/index.php/NVIDIA_Optimus#Display_Managers)

---

