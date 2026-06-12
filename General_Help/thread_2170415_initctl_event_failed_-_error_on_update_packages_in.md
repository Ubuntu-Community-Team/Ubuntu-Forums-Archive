---
title: "initctl: event failed - error on update packages in 22/08/13"
date: 2013-08-26
forum: General Help
---

### Post by albert11 on 2013-08-26
Hello everybody. I'm using ubuntu 12.04 LTS 64 bit.
it can't starts normaly. It stops just before to show the desktop, while I see the command lines...
The last command line is ** initctl: event failed**

The log file named lightdm.log says:
   [COLOR=#0000ff][+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.3, UID=0 PID=1747
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for automatic login as user avalldeperez
[+0.00s] DEBUG: Starting local X display
[+0.00s] DEBUG: X server :0 will replace Plymouth
[+0.03s] DEBUG: Using VT 7
[+0.03s] DEBUG: Activating VT 7
[+0.03s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.03s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.03s] DEBUG: Launching X Server
[+0.03s] DEBUG: Launching process 1781: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.03s] DEBUG: Waiting for ready signal from X server :0
[+0.03s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.03s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+0.65s] DEBUG: Process 1781 exited with return value 1
[+0.65s] DEBUG: X server stopped
[+0.65s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+0.65s] DEBUG: Releasing VT 7
[+0.65s] DEBUG: Stopping Plymouth, X server failed to start
[+0.66s] DEBUG: Display server stopped
[+0.66s] DEBUG: Stopping display
[+0.66s] DEBUG: Display stopped
[+0.66s] DEBUG: Stopping X local seat, failed to start a display
[+0.66s] DEBUG: Stopping seat
[+0.66s] DEBUG: Seat stopped
[+0.66s] DEBUG: Required seat has stopped
[+0.66s] DEBUG: Stopping display manager
[+0.66s] DEBUG: Display manager stopped
[+0.66s] DEBUG: Stopping daemon
[+0.66s] DEBUG: Exiting with return value 1[/COLOR]


The log file X.Olog.log says:
   [COLOR=#0000ff]X.Org X Server 1.13.0
Release Date: 2012-09-05
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
Current Operating System: Linux avalldeperez-P43-ES3G 3.5.0-39-generic #60~precise1-Ubuntu SMP Wed Aug 14 15:38:41 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-39-generic root=UUID=05180a06-ee70-4ffb-bd8e-355468179999 ro recovery nomodeset
Build Date: 11 April 2013  11:49:23PM
xorg-server 2:1.13.0-0ubuntu6.1~precise3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.24.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 26 11:06:00 2013
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
NVIDIA: API mismatch: the NVIDIA kernel module has version 319.32,
but this NVIDIA driver component has version 304.88.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.

Fatal server error:
no screens found
(EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
(EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
(EE)[/COLOR]

What can I do?
Thank you very much!
Albert.

---

### Post by rai_shu2 on 2013-08-26
Looks like your driver failed to install properly. Maybe take a look at this:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by albert11 on 2013-08-30
Hi rai_shu2, (and everybody)

I try to re-install the NVIDIA driver.
Now, I can start with the previus kernel version.
I started with the "previus linux version" in the boot menu, (on save mode), with the option "failsafeX", in low resolution of the screen.
I uninstall Nvidia drivers, and reistall the last version that appair (nvidia 319.updates).
Now, the computer start normaly, **but only in the previous linux version: 3.5.0.37**
I can't start the computer in normal mode yet. (3.5.0.39)

I try to acces in "Save mode. Only read mode" of the last kernel version, with the option "root", but I can't do anything in the command lines, because puts "only read mode"
How I can uninstall the nvidia drivers, from other USB live... or something like that?

Thank you very much!!

---

### Post by rai_shu2 on 2013-08-30
I think the problem is the version of the driver you have installed. The latest version in the repo that works with 12.04 is the nvidia 304.88 driver.

---

### Post by albert11 on 2013-09-08
It's solved:
I have uninstall the NVIDIA privative drivers from the control center of ubuntu. (System parameters -> hardware -> additonal drivers) 
Now, Ubuntu starts normaly.
There is some incompatibility with the new kernel 3.5.0.39 and 3.5.0.40, with the nvidia drivers. 

Thank you very much !!!
REgards

---

