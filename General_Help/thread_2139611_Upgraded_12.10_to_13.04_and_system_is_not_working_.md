---
title: "Upgraded 12.10 to 13.04 and system is not working after login"
date: 2013-04-27
forum: General Help
---

### Post by Palu on 2013-04-27
I upgraded to 13.04 from 12.10 yesterday--far too excited to remember to test with a live CD. :) So... everything looks fine up to the login screen, and then I log in. The system is "unresponsive". By that I mean I can see a gray (empty) panel along the top, a unity launcher on the left, and a desktop. The mouse moves. Right clicking, clicking and keyboard shortcuts do nothing. The unity launcher shows no animation with mouseover. Since nothing seems to be responsive, I'm not sure how I would access a terminal. There are no other system users to try out or other DMs installed for me to try logging into, so I can't simply go in with those.

An odd thing (and probably good) is that I CAN use sysreq reisub to reboot. **I can log on as a guest** as well, and there are no issues on "guest" except for my resolution maxing out lower than before I upgraded (1920:1080, which I swear is lower than it was before upgrade, but not 100% certain). I looked at a lot of other threads and most of them require you to troubleshoot with sudo privledges. Since I can only log on as a guest, I really don't know what to do besides "unity support test" and "lspci"... which I'll post below:

/usr/lib/nux/unity_support_test -p
```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1c.5 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 6 (rev c4)
00:1c.6 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 7 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Z77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)

```

lspci
```
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Desktop 
OpenGL version string:  3.0 Mesa 9.1.1

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

I **really** need the files in my (*encrypted*) home folder on my user account for my new job, and for what it's worth... my Minecraft server is installed there too. So I appreciate any help and I will stand by to do whatever you say. (stretches fingers in front of keyboard)

---

### Post by dino99 on 2013-04-27
Looks like a compiz crash; inside a terminal:

dconf reset -f /org/compiz/
compiz --replace ccp &
setsid unity

but you also can login with gnome (shell) which have a closed unity look & feel, and has less issue.

---

### Post by Palu on 2013-04-27
Thanks dino99. However, I cannot open a terminal since keyboard shortcuts are not doing anything, and I can't su from a terminal on guest since guest doens't have privledges.

---

### Post by Elfy on 2013-04-27
*Thread moved to **General Help**.*

---

### Post by pqwoerituytrueiwoq on 2013-04-27
[Ctrl]+[Alt]+F2
you can login to a tty and run the 1st command
then run startx and hope it works

this will add a terminal session as a alternative to unity, it may be of use to you
```
sudo sh -c 'echo "[Desktop Entry]\nVersion=1.0\nName=Terminal\nGenericName=Terminal Emulator\nExec=gnome-terminal --fullscreen\nIcon=utilities-terminal\nTerminal=false\nType=Application\nCategories=GTK;System;TerminalEmulator;Utility;\nStartupNotify=true" > /usr/share/xsessions/gnome-terminal.desktop'
```

---

### Post by grahammechanical on 2013-04-27
Emm, tricky.

Ctrl+Alt+T = not work
Ctrl+Alt+F2 = not work
Right click wallpaper + Change Desktop Background = not work. Pity. It opens System Settings and gives access to Software & Updates>Additional Drvier tab where we can change video drivers.
Recovery Mode>Resume = no work? That sometimes gets us to a desktop.
Recovery Mode>Failsafex = no work?

I am guessing that the issue is video driver. On that basis if the other methods are not working I suggest editing the boot parameters to include nomodeset.

At the Grub menu select Ubuntu and press E. Grub is now is Edit Mode. Look for the line that says: > initrd.lz quiet splash and insert nomodeset as in > initrd.lz nomodeset quiet splash

Press F10 to boot. See if that will get you to a desktop that will let you open additional drivers and change the video driver, and then open a terminal to reset unity or compiz. Oh, you could also try unplugging the keyboard and plugging back in. Might reset something regarding the keyboard. Desperate solutions sometimes work.

Regards.

---

### Post by Palu on 2013-04-27
The compiz reset command said "error spawning command line... reset a key or dir. -f is required for dirs" I would type out the whole thing, but I'm on a Kindle Fire to post here.

I tried all your stuff on one line in case it was on command that th forum split across lines. This time it gave the error and a warning that no display variable is set so it set it to :0. I ran startx and my screen is now just black... reboot and entry via Gui... it loads as originally (unresponsive except mouse) though my secondary monitor is pink. Odd...

---

### Post by Palu on 2013-04-27
Grah~ I went to the terminal from the logon screen and simply logged in without a DM, so that part works. I don't use GRUB btw or don't know how to get there because I don't have another OS.

---

### Post by dino99 on 2013-04-27
with a single OS installed, to get the grub menu, hold "shift" key down at bios end process; then you can choose the "recovery mode", activate the network, and run the commands given prior (each line given was a unique command)

---

### Post by Palu on 2013-04-27
Oh, I found an article that says Unity no longer uses dconf. Is that an issue with the command? Going to Grub like you said... will report.

---

### Post by dino99 on 2013-04-27
dconf is the ubuntu used tool (is your "article" can be trusted ?)

---

### Post by Palu on 2013-04-27
Grah, there is no line that says initrd.lz in my grub. There is a line with initrd (but no lz). It also isn't the line with quiet splash after it.

For

---

### Post by Palu on 2013-04-27
Dino99, no idea. :)

---

### Post by Palu on 2013-04-27
When pq recommended adding the terminal session as an option, did desktop entity mean something like "unity" or did it mean literally desktop entity with the brackets?

---

### Post by Palu on 2013-04-27
Dino. I tried the dconf reset command again. It doesn't work. I get 

error: Error spawning command line 'dbus-launch --autolaunch=6e7f04a39ef9b1268709e5a25132289e --binary-syntax --close-stderr': Child process exited with code 1

---

### Post by Palu on 2013-04-29
I still have the issue. I installed Lubuntu so I could access my main user with a DM that's working. I actually love Unity though, and I would appreciate any further help. :KS

---

### Post by Palu on 2013-05-05
Well... disappointed this time. Now I tried installing over my last install, but that didn't fix anything while making my LAMP server and Minecraft cease to function correctly. I'll use my Lubuntu stop-gap to back up my files for a hard drive wipe so I can revert to 12.10 and reinstall LAMP, but I can't figure out how to make a startup disk. My blank Dvds aren't mounting and the startup disk utility freezes before finishing a write to usb.

This is by far the most frustrated I've ever been on Linux, and it's very disheartening after my anticipation for 13.04.

---

