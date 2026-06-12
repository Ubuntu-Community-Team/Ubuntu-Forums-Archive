---
title: "issues upgrading graphics card"
date: 2007-10-20
forum: General Help
---

### Post by Pdavid on 2007-10-20
I recently upgraded my graphics card (nnvidia fx 5200 agp to 8600gt pcie), as well as my cpu (athlon 64 3500 to x2 4200) and added another GB of ram (now 2GB) and put a new hard drive in (though currently it's empty).

Anyway, after installing all the new bits, I booted it (wondering how much it would work), and it got to the boot prompt, I selected the default (Feisty) and it went one screen further, displaying some messages (the same as any boot, as far as I remember - something at the bottom, and "loading, please wait...." at the top) before the display cut out - it simply went blank and displayed "no signal" (I tried it with an older monitor too, same thing. Current monitor is a CHIMEI CMV 938D).

So, no worries, I though, I'll just try to boot into single user (recovery mode) - which worked fine, and I changed the driver in xorg.conf to 'nv'. I then successfully started x windows (by telinit 5) and I though "sweet!" so I rebooted it, only to find I still had the same issue with the default boot.

Now, I'm wanting to install Gutsy, and I have a live CD, so I thought I could just install this and not worry too much about the issues Feisty had, but after the live CD boot prompt, the same thing happens-but I do get a screen displaying "PCI:Cannot allocate resource to region 0 of device 00:00:00:01" (I'm not sure about that last code, it was something like that - a string of 0's ending in a 1). This seems to be fairly benign, I think - there was a bug in the linux kernel for something similar. Safe graphice mode also suffers from the same issue.

So I booted again to single user mode (and I'm not sure if I should have but) I downloaded new nvidia drivers and installed them (removing nvidia-glx first - it might be worth noting that my new graphics card doesn't show up in the restricted driver manager), and ran 

sudo dpkg-reconfigure -phigh xserver-xorg

after restarting X, even 3d acceleration was working (getting about 10k fps in glxgears), but it still wouldn't boot normally (I had to go through recovery mode).

Looking at xorg.conf, my card was labeled "Generic Graphics Card", while previously it recognised that it was a FX 5200, though nvidia-settings recognises it as an 8600gt.

booting into an old SUSE 10.1 got further, but couldn't start X with some errors - I think because the drivers weren't configured properly. Anyway, they were:

NVIDIA: No matching Device section for instance (BusID PCI:1:0:0) f(EE) No deviced detected

Fatal Server Error:
No screens found


(PCI:1:0:0 referrs to my graphics card, according to nvidia-settings)

I'm off to reboot to see if I can see anything in /var/log/messages

---

### Post by Lunarbunny on 2007-10-20
Same problem here. Upped my 7800GTX to a 8800GTS 640MB with 7.04, get no signal when trying to boot up first option, but recovery mode, either using root and [FONT="Lucida Console"]**startx**[/FONT] or continuing with Ctrl+D works fine. I managed to upgrade to 7.10 in recovery mode hoping that it might fix my issues with all the fancy new X stuff they threw in and no luck.

Note that if I try to use [FONT="Lucida Console"]**dpkg-reconfigure xserver-xorg**[/FONT] in recovery mode as root, it doesn't detect my monitor and names it the default.

I will try a few things (such as swapping ports on the card, screwing with [FONT="Lucida Console"]**/etc/X11/xorg.conf**[/FONT], etc.) and report back.

EDIT: As far as I can tell it has something to do with the bootsplash. By removing the [FONT="Lucida Console"]**quiet**[/FONT] and [FONT="Lucida Console"]**splash**[/FONT] arguments from the first entry (Ubuntu 7.10, kernel 2.6.22-14-generic)  [FONT="Lucida Console"]**/boot/grub/menu.lst**[/FONT], I was able to start normally, sans bootsplash. Anybody have clues on what might be the reason the bootsplash of all things is preventing EVERYTHING visual from working? Also, where are its settings, how might I replace it, etc? I do like to have a splash screen rather than flying lines of text.

---

### Post by Lunarbunny on 2007-10-20
[https://bugs.launchpad.net/ubuntu/+bug/86666](https://bugs.launchpad.net/ubuntu/+bug/86666) seems related but I have been unable to use the fix that a number of those using ATI cards seem to have gotten to work (setting the lilo mode to match the usplash.conf resolution, in my case 1280x1024 I added vga=795 at the end of my kernel line for grub.)

---

