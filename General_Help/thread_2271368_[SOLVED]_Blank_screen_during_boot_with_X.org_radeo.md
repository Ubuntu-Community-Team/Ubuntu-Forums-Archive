---
title: "[SOLVED] Blank screen during boot with X.org radeon drivers"
date: 2015-03-29
forum: General Help
---

### Post by simon94 on 2015-03-29
Right after the grub boot screen I get a blank screen and my monitor goes to standby with "No signal". But after some time the graphical login screen `sddm` will appear and I can log in and use KDE just fine. I'm currently running the latest Kubuntu 15.04 Beta 2.

I've tried both drivers, fglrx and the open radeon driver. With the fglrx driver I see the boot screen, but not with the radeon drivers.

I'd prefer to use the radeon drivers because I'm having graphical glitches with the fglrx drivers. Another problem with the fglrx driver I have is that I get a blank screen when switching to a virtual terminal.

Here are some infos:

Xorg.0.log: [http://pastebin.com/NM7zaPqm](http://pastebin.com/NM7zaPqm)

```
    simon@simon-kubuntu:~$ lspci -nnk | grep -i vga -A2
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cypress PRO [Radeon HD 5850] [1002:6899]
        Subsystem: ASUSTeK Computer Inc. Device [1043:0348]                                                                                                                                                                         
        Kernel driver in use: radeon     

```

How do I get my screen back during boot?

---

### Post by simon94 on 2015-03-30
No one? :-( If you need more information/logs please let me know. I'm a noob in this area and not sure what kind of information might help in debugging this issue. Thanks!

---

### Post by ProjectKITT on 2015-03-31
> **simon94 said:**
> Right after the grub boot screen I get a blank screen and my monitor goes to standby with "No signal". But after some time the graphical login screen `sddm` will appear and I can log in and use KDE just fine. I'm currently running the latest Kubuntu 15.04 Beta 2.

I've tried both drivers, fglrx and the open radeon driver. With the fglrx driver I see the boot screen, but not with the radeon drivers.

I'd prefer to use the radeon drivers because I'm having graphical glitches with the fglrx drivers. Another problem with the fglrx driver I have is that I get a blank screen when switching to a virtual terminal.

Here are some infos:

Xorg.0.log: [http://pastebin.com/NM7zaPqm](http://pastebin.com/NM7zaPqm)

```
    simon@simon-kubuntu:~$ lspci -nnk | grep -i vga -A2
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cypress PRO [Radeon HD 5850] [1002:6899]
        Subsystem: ASUSTeK Computer Inc. Device [1043:0348]                                                                                                                                                                         
        Kernel driver in use: radeon     

```

How do I get my screen back during boot?

Ah, I just switched from Kubuntu to Xubuntu, but maybe I can help... My screen would stay blank after the grub menu as well, up until the desktop suddenly appeared (mine's set to auto-login) and I fixed it by editing the GRUB file.

In the terminal, I entered ```
sudo gedit /etc/default/grub
``` and I removed the # symbol from in front of the line *GRUB_GFXMODE=1024x480*. Then I saved the file in gedit, and ran the command ```
sudo update-grub
``` in the terminal. Now I see the splash screen as it boots.

I'm not sure why that worked, and from what I understand is had something to do with the display driver (live boot had no such problem; it was only after the drivers were installed on my machine that it became an issue).

Maybe that will give you a place to start. Good luck! :)

---

### Post by simon94 on 2015-03-31
Hey, thanks a lot for the reply! I just tried it but unfortunately it didn't work :( I set GRUB_GFXMODE to 1024x768, and after a reboot the grub menu indeed had this resolution (everything was bigger than normal), but after that my screen went blank again until I was greeted by the login screen.

I have a 2560x1440 display, and without GRUB_GFXMODE the grub boot menu is displayed in the native resolution (fonts are tiny).

In the meantime I also found out about the "vbeinfo" command inside the grub shell. Unfortunately it doesn't seem to be possible to pipe the output to a file inside the grub shell, but I made photos with my smartphone and I think there is something wrong, because vbeinfo reports as max resoltion 1920x1440. It doesn't show the native 2540x1440 resolution.

Output of vbeinfo looks like this:

```
Adapter 'Cirrus CLGD 5446 PCI Video Driver':
  No info available
Adapter 'Bochs PCI Video Driver':
  No info available
Adapter 'VESA BIOS Extension Video Driver':
  VBE info:  version 3.0 OEM software rev: 12.20
  total memory: 16384 KiB
// here then comes a long list of resolutions, but native resolution isn't available
1024x768 x 8-32
1856x1393 x 8-32
// max reported resolution :(
1920x1440 x 8-32
  EDID version: 1.4
    Preferred mode: 2560x1440 // This is my native resolution
Adapter: 'VGA Video Driver':
  No info available
```

Any idea what might be wrong here? I suppose the driver won't load correctly, or something along those lines. I have no clue :( Another thing I noticed is that right after login, you get this funky animation, the default one in KDE5. And this exact animation runs really choppy and slow. But once the desktop is loaded everything is really fast, I have some animations enabled in kwin, turned on tearing prevention and everything just runs smooth. So I guess when I'm at the sddm login screen, the driver are not loaded yet correctly, only until I finally log in.

Could it be a problem that I previously had the fglrx driver installed, and now something is conflicting the the open radeon drivers? Are there any known conflicts when both drivers were installed at some point? Because when I switched from the fglrx driver to the xorg radeon driver through KDE's "Driver Manager", my desktop was really slow and not in native resolution. I had to uninstall some fglrx packages explicitly (I assumed this Driver Manager thingy would take care of this, since it asked me for my sudo password because it wanted to configure some packages).

So I think there might be the problem somewhere...

---

### Post by ProjectKITT on 2015-04-03
Oops, sorry for the delay... I didn't realize that I wasn't subscribed to this thread ^^;

Anyway, I don't really know much about drivers but just out of curiosity: if you boot Kubuntu from a live disk, then do you see the splash screen? I believe none of the proprietary drivers are loaded during a live boot.

---

### Post by simon94 on 2015-04-12
Hey ProjectKITT, now that's funny, I also didn't get a notification after your last reply! (but I got one on your first reply, weird!) So I didn't bother to check this thread, since I assumed nobody posted anything anyways :)

I cannot confirm right now that the Kubuntu logo shows up during boot off a live disk, because I'm using the USB drive I used for all my live Linux ISOs for something else now. But I seem to remember that I always saw a splash screen when booting from a live disk. Be it Kubuntu, Manjaro or the other distros I was trying out.

Anyway, I think that's a good point and I will try to free up another USB drive to confirm this, and maybe check the X.org log from the live system and compare it with mine.

It's really annoying to not see what's going on during boot, like if a filesystem check is going on, or something else... even more annoying is the fact that I seem to be the only one with such a problem, at least I simply can't find anything on the internet regarding this specific problem.

Last thing I tried was to specify the radeon driver and native solution of my display in an xorg.conf, but no luck unfortunately.

---

### Post by ProjectKITT on 2015-04-22
Yeah, it is really annoying when you can't see anything. I almost thought the monitor had quit working when it happened to mine o.O

I only found one thread that had the same problem, and unfortunately the OP didn't find the solution (it was one of those 'all of a sudden it works' kind of things... If only all problems fixed themselves!).

---

### Post by simon94 on 2015-04-30
I was finally able to this fix this. I added this line to /etc/default/grub:

```
GRUB_GFXPAYLOAD_LINUX=auto
```

Then "sudo update-grub2" and this brought back my kernel messages and splash screen :)

---

### Post by ProjectKITT on 2015-04-30
Hey, that's awesome! How did you figure it out?

And the funny thing is: I added that line to my GRUB as well, and now the splash screen is no longer dim. Yay! So let me say thank you very much for sharing your solution; who would've thought it would work for mine as well? :D

---

