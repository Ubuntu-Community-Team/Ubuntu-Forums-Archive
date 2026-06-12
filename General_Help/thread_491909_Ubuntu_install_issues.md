---
title: "Ubuntu install issues"
date: 2007-07-04
forum: General Help
---

### Post by vace117 on 2007-07-04
Hello.

I am very new and inexperienced with Ubuntu, so I hope someone will be able to give me a hand with these questions.

I just upgraded my workstation from Slackware to the latest Ubuntu and a lot of things are no longer working right from the start.

1) I run a lot of software in a VNC session b/c I mostly access it remotely. In Slackware i was able to run anything I wanted in a VNC session, but in Ubuntu Evolution and Thunderbird fail with this error:
```

The program 'evolution-2.10' received an X Window System error.
... etc ...

```

2) I was using Evolution 2.4 in Slackware. Evolution 2.10 in Ubuntu works, but so slowly that it is impractical to use it. My .evolution folder is a symlink to an NFS share, but the NFS transfer speed is not the bottleneck here (I checked by copying files). Every action results in a "Storing folder..." or "Receiving message ###..." message that takes about 30 seconds to complete. I do have a lot of messages in my folders, but it worked with reasonable speed before.... Did anyone else run into this?

3) I have a computer on my LAN that used to connect to my workstation via XDMCP. This no longer works in Ubuntu. The client clearly connects, b/c the login screen appears for about 2 seconds, but then it restarts and keeps trying to connect indefinitely with the screen popping up for a few seconds and then restarting. There are no obvious errors in the xorg log. Is there a way to turn on more XDMCP debugging on either the client or the server to figure out why the connection is broken after a few seconds?

4) grub is not being consistent with drive naming. My OS is installed on /dev/hdb1 and when the system is running grub sees it as (hd1,0):
```

grub>  find /boot/grub/stage1
 (hd1,0)

```

However, during boot time /dev/hdb somehow becomes (hd0) in grub! I really don't understand why this would happen. I suppose I could change /boot/grun/menu.lst to say "root (hd0,0)", but then I would have to remember to do that every time menu.lst is update automatically.

5) The native NVIDIA driver from nvidia-glx package doesn't work the same way as it did in Slackware. I copied my xorg.conf files from Slackware for both Twin and Dual Head (two X servers) configurations exactly, but in Ubuntu my CRT monitor is confined to 800x600 and I can't seem to do anything about it in both TwinView and Dual Head.

6) The system freezes during shutdown and I have to reset the computer. I think the freeze happens before the file systems are unmounted, b/c there are a lot of journaslrecovered during the next boot up.

The items 1 to 3 are very critical for me and I hope I will be able to figure out how to fix them in Ubuntu before I am forced to go back to Slackware.

Any advise would be greatly appreciated.

---

### Post by vace117 on 2007-07-04
With regards to programs crashing in VNC sessions...

I uninstalled vnc4server package and downloaded a version of VNC from the VNC site. The programs do not crash in that version of VNC. However. the XVnc process crashes after the first client disconnects and I can't find any error messages in the logs to tell me why. So this doesn't get me any closer either :(

---

### Post by vace117 on 2007-07-04
I found a solution to the VNC problem here:
[https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/78887](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/78887)

with more detail available here:
[https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/110263](https://bugs.launchpad.net/ubuntu/+source/vnc4/+bug/110263)

Now just the Evolution and XDMCP problems remaining before I can take a deep breath and try to figure out the NVIDIA and shutdown problems at a more leisurely pace :)

---

### Post by vace117 on 2007-07-04
In order to make Evolution go at a decent speed I had to install 'nfs-common' package. Now it is as fast as it was in Slackware.

---

### Post by vace117 on 2007-07-05
I got a bit more information about the XDMCP problem.

Firstly, I was able to successfully use XDMCP with another, much newer workstation that is now also running Feisty. So, the problem is clearly with the X server on the other remote machine. It is not an Ubuntu install but still, I would really appreciate some suggestions.

I do not believe that the problem is with XDMCP, but rather with the communication with the X server on the remote machine. I used wireshark to look at the communication and it looks like some X events cause the server to partially restart. This is the part of the Xorg.0.log that keeps repeating.
```

(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VbeVersion is 258, OemStringPtr is 0xc000260d,
        OemVendorNamePtr is 0x01040103, OemProductNamePtr is 0x01010100,
        OemProductRevPtr is 0x01110105
(II) VESA(0): VESA VBE Version 1.2
(II) VESA(0): VESA VBE Total Mem: 1024 kB
(II) VESA(0): VESA VBE OEM: Cirrus Logic GD-5436 VGA
(II) VESA(0): virtual address = 0x404b0000,
        physical address = 0xa0000, size = 65536
(==) VESA(0): Default visual is PseudoColor
(==) RandR enabled

```

In the packet sniffer I can see that the last thing that happens before the XDMCP communication starts all over again is the remote host sending this to the Ubuntu server:
```

Event: DestroyNotify, UnmapNotify, EnterNotify, DestroyNotify

```

I really don't know how to interpret this information, so any ideas would be welcome. Thanks.

---

### Post by vace117 on 2007-07-05
I was able to use a workaround for the grub issue. 

The bug is described here:
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497)

In my case the drive that is seen by grub as (hd1) when the system is running appears as (hd0) to grub during bootup.

As a workaround I opened /boot/grub/menu.lst and changed the 'groot' line to read:
```

# groot=(hd0,0)

```

Note that the line is supposed to stay commented out. The 'update-grub' tool actually reads these commented values when it is generating a new /boot/grub/menu.lst.

This way I don't have to remember to change (hd1,0) to (hd0,0) after every automatic menu.lst update.

---

### Post by vace117 on 2007-07-05
I tracked the shutdown problem to the incorrect order of the shut down scripts. It turned off openvpn and some time later tried to unmount the nfs shares, which are running on an openvpn tunnel. 

So this was just a matter of changing the order of the shutdown scripts.

This takes care of the easy ones. I still have no clue about the XDMCP problem and would appreciate any help.

---

### Post by vace117 on 2007-07-06
The NVIDIA driver was restricting my CRT monitor to 800x600 b/c the monitor supplied invalid EDID data, so there were no modes in the Mode Pool for that monitor. When the mode pool is empty the driver defaults to 800x600.

I solved it by disabling a lot of checks that are performed on each graphical mode before it is added to the mode pool. The relevant section of xorg.conf is:
```

Section "Device"   
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 Ti 4200"
EndSection

Section "Screen"   
    Identifier     "Screen0"
    Device         "Device0"
    DefaultDepth    24
    Option "ConnectedMonitor"           "DFP-0, CRT-1"    
[COLOR="Red"]    Option "ModeValidation" "CRT-1: NoVertRefreshCheck, NoDFPNativeResolutionCheck, NoMaxPClkCheck, NoEdidMaxPClkCheck, NoHorizSyncCheck, NoVirtualSizeCheck;"[/COLOR]
    Option "TwinView"
    Option "HorizSync"          "DFP-0: 30-85; CRT-1: 30-85"
    Option "VertRefresh"        "DFP-0: 50-120; CRT-1: 48-120"
    Option "MetaModes"          "DFP-0: 1680x1050, CRT-1: 1280x960; DFP-0: 1280x960, CRT-1: 1280x960; DFP-0: 800x600, CRT-1: 800x600"
    Option "TwinViewOrientation"        "CRT-1 LeftOf DFP-0"
[COLOR="Blue"]    Option "TwinViewXineramaInfoOrder" "DFP-0"[/COLOR]

    SubSection     "Display"
        Depth       24
        Modes   "1680x1050" "1280x960" "800x600"
    EndSubSection
EndSection

```

Note that by specifying "TwinViewXineramaInfoOrder" I am setting my flat panel as the primary Gnome monitor. By default Gnome would have used the CRT.

---

