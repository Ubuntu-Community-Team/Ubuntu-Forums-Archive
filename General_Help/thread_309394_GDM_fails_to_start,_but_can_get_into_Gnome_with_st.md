---
title: "GDM fails to start, but can get into Gnome with startx"
date: 2006-11-29
forum: General Help
---

### Post by ni2sml on 2006-11-29
A few days ago I had a hard lockup and had no option but to kill the power (couldn't even ssh in). Ugh... :(

Some files must have been corrupted in the crash, and now GDM won't start. What's odd about it is, I can log in at the console, run "startx" and get into Gnome, complete with hardware 3D acceleration. So, X is apparently fine.

Trying to start GDM, the system starts X, gets into the correct resolution with a black screen, displays the spinning "wait" pointer for a few seconds, then bails out to the console. It retries again after a couple more seconds, and keeps doing this until the system decides it's had enough and displays the "failed to start too many times" blue screen.

The GDM log looks like this:

```

/var/log/gdm  paul@transam:pts/1  0 jobs   8:39PM
% cat :0.log

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux transam 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 07 July 2006
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 28 19:15:51 2006
(==) Using config file: "/etc/X11/xorg.conf"
(**) RADEON(0): RADEONPreInit
(**) RADEON(0): RADEONScreenInit e0000000 0
(**) RADEON(0): Map: 0xe0000000, 0x04000000
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x81fdbc0)
(**) RADEON(0): Read: 0x00000006 0x00010047 0x00000000
(**) RADEON(0): Read: rd=6, fd=71, pd=1
(**) RADEON(0): RADEONSaveMode returns 0x81fdbc0
(**) RADEON(0): DRI New memory map param
(**) RADEON(0): RADEONInitMemoryMap() :
(**) RADEON(0):   mem_size         : 0x04000000
(**) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1600x1200     160.00  1600 1656 1848 2112  1200 1201 1204 1250 (24,32)
1600x1200     160.00  1600 1656 1848 2112  1200 1201 1204 1250 (24,32)
(**) RADEON(0): Pitch = 13107400 bytes (virtualX = 1600, displayWidth = 1600)
(**) RADEON(0): RADEONInit returns 0x81fe570
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81fe570)
(**) RADEON(0): RADEONRestoreMemMapRegisters() :
(**) RADEON(0):   MC_FB_LOCATION   : 0xe3ffe000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): GRPH_BUFFER_CNTL from 20077c7c to 20165c5c
(**) RADEON(0): RADEONSaveScreen(0)
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(**) RADEON(0): Initializing backing store
(**) RADEON(0): DRI Finishing init !
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): GRPH_BUFFER_CNTL from 20077c7c to 20165c5c
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 200
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): Initializing DPMS
(**) RADEON(0): Initializing Cursor
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(**) RADEON(0): RADEONScreenInit finished
error opening security policy file /usr/lib/xserver/SecurityPolicy
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc104)+us" };
    xkb_geometry             { include "pc(pc104)" };
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
(**) RADEON(0): RADEONSaveScreen(2)
Synaptics DeviceOff called
(**) RADEON(0): RADEONLeaveVT
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81fdbc0)
(**) RADEON(0): RADEONRestoreMemMapRegisters() :
(**) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000
(**) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Ok, leaving now...

```

Tried (completely) uninstalling and reinstalling GDM. Restored /etc/gdm from a good backup. Looked for lockfiles and didn't spot anything obvious. Tried "sudo dpkg-reconfigure gdb".

No luck. ](*,)

gdmsetup also fails, I'm thinking there might be some common breakage here? Trying to run it from a terminal in Gnome I get this:

```

% sudo gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.

```

The config files in /etc/gdm appear to be in good shape.

Next step is probably to check the permissions and condition of files involved in starting GDM, or reinstall Gnome entirely. After that, the "universal reconfiguration tool" (24lb sledgehammer) will be starting to look more appealing... :twisted:

I feel like I'm overlooking *something* obvious, so any suggestions where to look next would be greatly appreciated!

---

### Post by barlaso on 2007-02-03
Hey, I'm having the exact same problem after playing around with 3d-desktop packages like beryl and compiz for a few days, suddenly gdm wouldn't start anymore.  startx works, I can use everything as normal as long as i dont restart.  If i restart, gdm fails to load after displaying the 'wait' pointer.

I was wondering if a solution to this was found?

---

### Post by barlaso on 2007-02-03
Ok my problem was solved.  Apparently the /etc/X11/gdm/gdm.conf-custom file was configured to start Xgl server by default.  The Xgl server was failing to load for some reason. 

I commented out the xgl related lines from /etc/X11/gdm/gdm.conf-custom:
[servers]# Override display 1 to use Xgl
#0=Xgl 

#[server-Xgl] 
#name=Xgl server 
#command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
#flexible=true

I still dont know why Xgl was failing, but at least I got my login manager back.

---

