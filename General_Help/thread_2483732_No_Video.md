---
title: "No Video"
date: 2023-02-07
forum: General Help
---

### Post by jgw on 2023-02-07
I was trying to play a movie.  First I tried KODI.  The picture part of the movie was a black screen.  The entire screen was not completely black.  It was still displaying system stuff and notifications with no problem.  Audio was also fine.  So, I then tried VLC and also the Ubuntu video viewer.    Got the same from all of those too.  Oh, I also went to CNN to watch one of their videos and that worked fine.  

Thoughts?

---

### Post by monkeybrain20122 on 2023-02-07
What is your graphic card? Run

```
lshw -C display
```

and post the output.

---

### Post by jgw on 2023-02-07
Thank you..........

reg@greg2:~$ sudo lshw -C display
[sudo] password for greg: 
  *-display                 
       description: VGA compatible controller
       product: RS780L [Radeon 3000]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: /dev/fb0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=radeon latency=0 resolution=1920,1080
       resources: irq:18 memory:d0000000-dfffffff ioport:d000(size=256) memory:fe9f0000-fe9fffff memory:fe800000-fe8fffff memory:c0000-dffff
greg@greg2:~$

---

### Post by Claus7 on 2023-02-07
Hello,

I would try also mpv as both videos and vlc in the last ubuntu versions have problems. Just a quick proposal.

Regards!

---

### Post by jgw on 2023-02-07
Thank you..........

I will try this but, first,install MPV and when I try, with "sudo apt install mpv"" I get "Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 8806 (apt)" which has suddenly appeared and won't let me do anything.  Read I could fix it with "dpkg --configure -a" but that didn't help.

---

### Post by jgw on 2023-02-07
Thank you..........

I will try this but, first,install MPV and when I try, with "sudo apt install mpv"" I get "Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 8806 (apt)" which has suddenly appeared and won't let me do anything.  Read I could fix it with "dpkg --configure -a" but that didn't help.

---

### Post by monkeybrain20122 on 2023-02-07
> **jgw said:**
> Thank you..........

I will try this but, first,install MPV and when I try, with "sudo apt install mpv"" I get "Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 8806 (apt)" which has suddenly appeared and won't let me do anything.  Read I could fix it with "dpkg --configure -a" but that didn't help.

That just means another instance of apt is running, probably checking updates or whatnot, just wait a few minutes it will go away, or maybe you have synaptic open, in that case just close it.

**Edited**: if you have mpv, open a video in the command line like

```
mpv /path/to/video
```

The error messages (if any) may be helpful

Sorry, I don't have any experience with amd graphic cards so can't give you much help.

---

### Post by jgw on 2023-02-07
Thank you......

I installed and ran mpv and it didn't help.

than I moved a couple of videos to a memory stick and ran them in another ubuntu machine.  It didn't start until I installed all multimedia codecs with sudo apt install ubuntu-restricted-extras.  then I tried and everything ran on this machine but its different from the one with the problem.  I am sticking with that one as its worked for several years but I blew it up but thought I had it fixed.  Now I know its the machine and that's something.  I also suspect that I have cleverly changed something that I should not have.  Now I have to figure what that might be.  

I have installed the ubuntu restricted extra stuff but it made no difference.  I wonder if there is more of that to do.  

One of the problems with the problem machine is that it doesn't have an additional driver.  The machine graphics is AMD® Rs780 Resolution: 1920x1080 pixels and I think I can goto amd and find another driver, we will see about that one.

I just checked out the amd drivers.  Seems they have some new ones out for ubuntu 22.20  I guess I could update from 22.04 but perhaps I don't have to.  I continue to investigate.

Here is some info on this:

```
reg@greg2:~$ sudo lshw -c video
[sudo] password for greg: 
  *-display                 
       description: VGA compatible controller
       product: RS780L [Radeon 3000]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5
       bus info: pci@0000:01:05.0
       logical name: /dev/fb0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=radeon latency=0 resolution=1920,1080
       resources: irq:18 memory:d0000000-dfffffff ioport:d000(size=256) memory:fe9f0000-fe9fffff memory:fe800000-fe8fffff memory:c0000-dffff
greg@greg2:~$

```

So, should I swap out drivers?  What things should I be checking to find out what is causing video pictures to go away?

---

### Post by jgw on 2023-02-08
thanks for the help (made me think)

I had some display cards and so I took one (nvidia) and installed it and now I have pictures again.  I have no idea what happened.

---

### Post by jgw on 2023-02-09
thought I should mention that now, when running KODI I have everything but every time I press the backslash it turns the display in the 1/4 display size. So that is now my new battle - I will post in Kodi and see what happens.

---

### Post by jgw on 2023-02-10
greg@greg2:~$ sudo lshw -C display
[sudo] password for greg: 
  *-display                 
       description: VGA compatible controller
       product: GF108 [GeForce GT 440]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:43 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:dc00(size=128) memory:c0000-dffff
  *-graphics
       product: VESA VGA
       physical id: 1
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=640,480
greg@greg2:~$

---

### Post by jgw on 2023-02-10
Now using: NVIDIA drivr metapackage from nvidia-driver-390 (proprietary, tested)

greg@greg2:~$ sudo lshw -C display
[sudo] password for greg: 
  *-display                 
       description: VGA compatible controller
       product: GF108 [GeForce GT 440]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:43 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:dc00(size=128) memory:c0000-dffff
  *-graphics
       product: VESA VGA
       physical id: 1
       logical name: /dev/fb0
       capabilities: fb
       configuration: depth=32 resolution=640,480
greg@greg2:~$

---

### Post by jgw on 2023-02-10
I now find that some shows can be seen and other cannot.  I can always see with Videos and VLC but Kodi is a bit choosy.  I suspect that I need more vid stuff like the ubuntu  restricted extras or I have something set wrong in Kodi.

---

