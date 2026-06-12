---
title: "Screen Resolution"
date: 2006-11-05
forum: General Help
---

### Post by HanaD on 2006-11-05
hi,
i ma using Kubuntu,

i changed my screen resolution settings on last log on to 800x600 from higher resolution.

however now when i log in the screen resolution is 640x800 and i do not have any other option for screen resolution in system settings>>>>monitor and display..only one option of 640x800 is there..

how can i get other options??? which i had earlier [800x600, 1074x768]

please advise..

Regards,
Hana

---

### Post by babooka on 2006-11-05
Two options:

1) sudo gedit /etc/X11/xorg.conf

Should have something like this:
where modes is a list of available resolutions
      SubSection "Display"
                Depth           24
                Modes            "1024x768" "800x600" "640x480"
        EndSubSection


2) sudo dpkg-reconfigure xserver-xorg

This will change xorg.conf file, one of the steps is choosing available resolutions

---

### Post by HanaD on 2006-11-05
I tried both methods, problem still persists..same resol;ution 640x800

this is from the terminal


gag@Jaguar:~$ sudo dpkg-reconfigure xserver-xorg
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN6> line 13.
xserver-xorg postinst warning: not updating /etc/X11/X; file has been
   customized
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20061106034820
dexconf: error: cannot generate configuration file; shared/default-x-server not 
set.  Aborting.  Reconfigure the X server with "dpkg-reconfigure" to correct 
this problem.
xserver-xorg postinst warning: error while preparing new Xorg X server
   configuration file in /etc/X11/xorg.conf.dpkg-new; not attempting to
   update existing configuration
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
gag@Jaguar:~$ dpkg-reconfigure
/usr/sbin/dpkg-reconfigure must be run as root
gag@Jaguar:~$ sudo dpkg-reconfigure
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
/usr/sbin/dpkg-reconfigure: please specify a package to reconfigure
DESTROY created new reference to dead object ' Qt::VBoxLayout' during global destruction.
gag@Jaguar:~$ clear

gag@Jaguar:~$ sudo dpkg-reconfigure xserver-xorg
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN6> line 13.
xserver-xorg postinst warning: not updating /etc/X11/X; file has been
   customized
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20061106034945
dexconf: error: cannot generate configuration file; shared/default-x-server not 
set.  Aborting.  Reconfigure the X server with "dpkg-reconfigure" to correct 
this problem.
xserver-xorg postinst warning: error while preparing new Xorg X server
   configuration file in /etc/X11/xorg.conf.dpkg-new; not attempting to
   update existing configuration
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.

---

