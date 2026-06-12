---
title: "How to tell Compiz to use integrated graphics rather than a GPU?"
date: 2014-11-13
forum: General Help
---

### Post by mila2 on 2014-11-13
Hi everyone,

I've been bugging multiple forums with my problems, but I think this might be the best place to ask. My goal is to basically:

- Get Ubuntu (14.04LTS) to use integrated graphics only
- Use my GPU (GTX650) for debugging only (doesn't work if it is used for display)

I've set up 10-monitors.conf to look like:
```
Section "Monitor"
    Identifier     "VGA1"
EndSection

Section "Monitor"
    Identifier     "HDMI2"
EndSection

Section "Device"
   Identifier      "intel0"
   Driver          "intel"
   BusID           "PCI:0@0:2:0"
EndSection

Section "Device"
   Identifier      "intel1"
   Driver          "intel"
   BusID           "PCI:0@0:2:0"
EndSection

Section "Screen"
   Identifier     "Screen0"
   Device         "intel0"
   Monitor        "VGA1"
   DefaultDepth   24
   SubSection     "Display"
      Depth       24
      Modes       "1680x1050" "1920x1080"
   EndSubSection
EndSection

Section "Screen"
   Identifier     "Screen1"
   Device         "intel1"
   Monitor        "HDMI2"
   DefaultDepth   24
   SubSection     "Display"
      Depth       24
      Modes       "1680x1050" "1920x1080"
   EndSubSection
EndSection

```

My displays work (both plugged into the motherboard, no signal comes out of the GPU). I switched the setting in BIOS to use iGPU by default.

Anyway, if I run ```
lsof /dev/nvidia*
```, it tells me that compiz is still using nvidia:

```
cinnamon@cinnamon:~$ lsof /dev/nvidia*
COMMAND  PID     USER   FD   TYPE  DEVICE SIZE/OFF  NODE NAME
compiz  1636 cinnamon  mem    CHR 195,255          10738 /dev/nvidiactl
compiz  1636 cinnamon  mem    CHR   195,0          10739 /dev/nvidia0
compiz  1636 cinnamon   11u   CHR 195,255      0t0 10738 /dev/nvidiactl
compiz  1636 cinnamon   12u   CHR   195,0      0t0 10739 /dev/nvidia0
compiz  1636 cinnamon   13u   CHR   195,0      0t0 10739 /dev/nvidia0
compiz  1636 cinnamon   14u   CHR   195,0      0t0 10739 /dev/nvidia0
```

So that's not the best and my debugger still won't work. Here is a printout of 
```
 lspci | grep VGA 
```, so you know both of them are there:

```
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GTX 650] (rev a1)

```

How can I stop compiz from using my Nvidia card and just use the integrated one?

[PS. This is my old post on AskUbuntu that has more details about what I've done with xorg.conf.]("http://askubuntu.com/questions/547769/configure-xorg-to-work-from-integrated")

Thanks in advance!

---

