---
title: "Fun with udev rules failing"
date: 2008-06-04
forum: General Help
---

### Post by unutbu on 2008-06-04
I am trying to use udev rules to run a program whenever I plug in a camera to the computer.

1. I plug in camera to computer via USB cable
2. Borrowing a line from [http://ubuntuforums.org/archive/index.php/t-375010.html](http://ubuntuforums.org/archive/index.php/t-375010.html)
```
for dev in `ls /sys/bus/usb/devices`; do udevinfo -ap /sys/bus/usb/devices/$dev; done > ~/tmp/udevinfo.txt
```

In udevinfo.txt I find
```

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb8/8-4':
    KERNEL=="8-4"
    SUBSYSTEM=="usb"
    DRIVER=="usb"
    ATTR{product}=="Canon Digital Camera"
...
[B]    ATTR{idProduct}=="3110"
    ATTR{idVendor}=="04a9"[/B]

```

3. Based on the above info I create /etc/udev/rules.d/53-local.rules:

```
  /etc/udev/rules.d:
  -rw-r--r-- 1 root root   195 2008-06-04 22:18 53-local.rules

% cat /etc/udev/rules.d/53-local.rules 
ATTR{idProduct}=="3110", ATTR{idVendor}=="04a9", RUN+="/home/heart/bin/dl-pictures.pl"
```

4. I turn off camera
5. I turn on camera, expecting dl-pictures.pl to run, but no joy. Why no joy? Why? :)

6. So I try
```
% sudo udevcontrol reload_rules
```

7. Turn camera off/on, but still no joy.

---

### Post by spiderbatdad on 2008-06-04
> Files in /etc/udev/rules.d/ are parsed in lexical order, and in some circumstances, the order in which rules are parsed is important. In general, you want your own rules to be parsed before the defaults, so I suggest you create a file at /etc/udev/rules.d/10-local.rules and write all your rules into this file.
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

---

### Post by unutbu on 2008-06-05
Hi spiderbatdad! Thanks for that.
I tried it:
```
  -rw-r--r-- 1 root root   195 2008-06-04 22:18 10-local.rules
```
But still no go.

The reason why I chose 53 was because of 
/etc/udev/rules.d/README:
```

This scheme has been chosen so that user-supplied rules are normally
named 50-*.rules for the right thing to happen.
```

and 50 was already taken.

```
  -rw-r--r-- 1 root root  5716 2007-09-15 22:05 50-xserver-xorg-input-wacom.rules
  -rw-r--r-- 1 root root   980 2008-02-05 00:34 55-hpmud.rules
```

---

### Post by spiderbatdad on 2008-06-05
I had seen that readme, as well, and then found the above documentation. Have you tried assigning 50 instead of 53? Should not be an issue. I have 2 udev rules with an order of 50. Of course the file names are not the same.

---

### Post by sdennie on 2008-06-05
Have you tried using udevtest to try and debug the problem?  The end of the guide that spiderbatdad linked shows how to do it.  Also, I'm not completely sure if two ATTR rules are enough (maybe they are though) so, you may need to add something like SUBSYSTEM="usb".

---

### Post by unutbu on 2008-06-05
Thanks for the suggestions, spiderbatdad and vor.
So far I've tried 10, 50, 53 and 83. In no case does my script run. 

To run udevtest I need to specify the device path. Since I don't know the exact device path, I turned on the camera and ran this:

```
% for dev in `ls /sys/bus/usb/devices`; do echo "probing /sys/bus/usb/devices/$dev"; echo "udevinfo -ap /sys/bus/usb/devices/$dev"; udevinfo -ap /sys/bus/usb/devices/$dev; echo "udevtest /sys/bus/usb/devices/$dev"; udevtest /sys/bus/usb/devices/$dev; done > ~/tmp/udev.dat
```

I then searched ~/tmp/udev.dat  for the string "Camera", and came up with this:

```

probing /sys/bus/usb/devices/4-3
**udevtest /sys/bus/usb/devices/4-3**
parse_file: reading '/etc/udev/rules.d/00-init.rules' as rules file
...
parse_file: reading '/etc/udev/rules.d/45-libgphoto2.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libsane.rules' as rules file
parse_file: reading '/etc/udev/rules.d/50-local.rules' as rules file
parse_file: reading '/etc/udev/rules.d/50-xserver-xorg-input-wacom.rules' as rules file
parse_file: reading '/etc/udev/rules.d/55-hpmud.rules' as rules file
...
import_uevent_var: import into environment: 'MAJOR=189'
import_uevent_var: import into environment: 'MINOR=388'
import_uevent_var: import into environment: 'DEVTYPE=usb_device'
import_uevent_var: import into environment: 'DRIVER=usb'
import_uevent_var: import into environment: 'PHYSDEVBUS=usb'
import_uevent_var: import into environment: 'PHYSDEVDRIVER=usb'
import_uevent_var: import into environment: 'DEVICE=/proc/bus/usb/004/005'
import_uevent_var: import into environment: 'PRODUCT=4a9/3110/2'
import_uevent_var: import into environment: 'TYPE=0/0/0'
import_uevent_var: import into environment: 'BUSNUM=004'
import_uevent_var: import into environment: 'DEVNUM=005'
main: looking at device '/devices/pci0000:00/0000:00:1d.7/usb4/4-3' from subsystem 'usb'
udev_rules_get_name: no node name set, will use kernel name '4-3'
udev_db_get_device: found a symlink as db file
udev_device_event: device '/devices/pci0000:00/0000:00:1d.7/usb4/4-3' already in database, cleanup
udev_node_add: creating device node '/dev/4-3', major=189, minor=388, mode=0660, uid=0, gid=0
**main: run: '/home/heart/bin/dl-pictures.pl'**
main: run: 'socket:/org/freedesktop/hal/udev_event'
main: run: 'socket:/org/kernel/udev/monitor'
```

I don't know what to make of this. It looks like dl-pictures.pl is in the queue of programs to be run, but it isn't getting executed (I know for certain because a certain file is not getting created).

I notice that the other strings in the run queue have a different format: they all begin with "socket:" followed by a path, but not to a script or executable. Is this where I am going wrong?

PS. I also notice that if I wait for a few minutes and then run the same looping udevtest command, there is no output related to the camera, even though it is still plugged in and turned on. Is this as it should be?

---

### Post by sdennie on 2008-06-05
Is it possibly a permissions problem?  Could the user the udev script is being run as not have read or execute permissions to the script?

---

### Post by Kernel_Krunch on 2008-06-05
use `udevadm trigger` to do a manual udev run.  You might have the other rules over-riding yours so use the "final rule" option... can't remember what that is off the top of head.

hope it helps

---

### Post by unutbu on 2008-06-05
Kernel_Krunch, thanks for the heads-up regarding udevadm. 

Vor, thanks for pointing out the permission issue. I moved the script to /tmp, edited it so it wasn't trying to write to my home account and then it ran fine.

Now I'd like to know what user is running the script. I believe it isn't root, since root could have written to my account. 

To find out I edited the dl-pictures.pl script to include 
```

system("whoami > .dl-pictures-executed");
```

and found .dl-pictures-executed contained 'root'. 

My goodness. Now I'm confused again. 

Do you know what user runs udev rules scripts?
If it is root, why didn't the script work before moving it to /tmp?

If it is not root, why did whoami return root?

---

### Post by Kernel_Krunch on 2008-06-05
> **unutbu said:**
> 
Do you know what user runs udev rules scripts?
If it is root, why didn't the script work before moving it to /tmp?

If it is not root, why did whoami return root?

always root unless you su it.

could be the fake root i see... not sure.  Glad to hear it works now ;)

---

### Post by mc4man on 2008-06-05
@ unutbu 
Just curious if it's now working the way you wanted. I had tried something similar, the script was designed to dl to home -> pictures and create a new sub dir. based on the exif date info. The closest I came was the script ran but the folder was owned by root. Considering my lack of know how that was a dead end. My low rent solution was to put the script in the home dir. and replace the auto dl. command in removable drives... with ./<script>

---

### Post by unutbu on 2008-06-06
I spoke too soon.

1) I can get udev to execute a script as a normal user.
2) I can write files to my home directory (no permission problems).
3) I can **not** get gphoto2 to download pictures when run through a script called by udev
4) I can get gphoto2 to download pictures when the same script is run manually.

Here is my current non-working setup:

```
% ls -l /etc/udev/rules.d/50-local.rules
-rw-r--r-- 1 root root 109 2008-06-06 16:49 /etc/udev/rules.d/50-local.rules

% cat /etc/udev/rules.d/50-local.rules
ATTR{idProduct}=="3110", ATTR{idVendor}=="04a9", RUN+="/bin/su heart -c '/home/heart/bin/dl-pictures.sh'"


% ls -l /home/heart/bin/dl-pictures.sh
-rwxr-xr-x 1 heart heart 207 2008-06-06 16:53 /home/heart/bin/dl-pictures.sh

% cat /home/heart/bin/dl-pictures.sh
#!/bin/sh
cd /home/heart/images/XTi
/usr/bin/gphoto2 --port usb: --force-overwrite --get-all-files --debug --debug-logfile /home/heart/images/XTi/.debug
env > /home/heart/images/XTi/.dl-pictures-executed

```
When I turn on the camera, two files are created:

```
  /home/heart/images/XTi:
  -rw-r--r--   1 heart heart 114392 2008-06-06 16:58 .debug
  -rw-r--r--   1 heart heart    501 2008-06-06 16:58 .dl-pictures-executed
```

but no pictures are downloaded.

If I then run the command manually, the pictures are downloaded:

```
16:54:34 heart@tack:~% cd images/XTi/
16:59:14 heart@tack:~/images/XTi% mkdir save
16:59:35 heart@tack:~/images/XTi% mv .d* save
16:59:55 heart@tack:~/images/XTi% which dl-pictures.sh
/home/heart/bin/dl-pictures.sh
17:00:18 heart@tack:~/images/XTi% dl-pictures.sh
Downloading 'IMG_1711.JPG' from folder '/store_00010001/DCIM/100CANON'...
Saving file as IMG_1711.JPG
Downloading 'IMG_1712.JPG' from folder '/store_00010001/DCIM/100CANON'...
Saving file as IMG_1712.JPG
Downloading 'IMG_1713.JPG' from folder '/store_00010001/DCIM/100CANON'...
Saving file as IMG_1713.JPG

  /home/heart/images/XTi:
  total used in directory 32492 available 267243088
  drwxr-xr-x   3 heart heart     4096 2008-06-06 17:00 .
  drwxr-xr-x 139 heart heart     4096 2008-06-06 16:56 ..
  -rw-r--r--   1 heart heart 27197638 2008-06-06 17:00 .debug
  -rw-r--r--   1 heart heart     1614 2008-06-06 17:00 .dl-pictures-executed
  -rw-r--r--   1 heart heart  2520973 2008-06-06 17:00 IMG_1711.JPG
  -rw-r--r--   1 heart heart   900908 2008-06-06 17:00 IMG_1712.JPG
  -rw-r--r--   1 heart heart  2582177 2008-06-06 17:00 IMG_1713.JPG
  drwxr-xr-x   2 heart heart     4096 2008-06-06 16:59 save

```

When gphoto2 fails to download pictures, the last part of the .debug file contains this:

```
0.458133 gphoto2-camera(2): Setting abilities ('Canon EOS 400D (PTP mode)')...
0.458146 gphoto2-setting(2): Setting key 'model' to value 'Canon EOS 400D (PTP mode)' (gphoto2)
0.458158 gphoto2-setting(2): Saving 2 setting(s) to file "/home/heart/.gphoto/settings"
0.458242 gphoto2-port-info-list(2): Looking for path 'usb:' (11 entries available)...
0.458258 gphoto2-port-info-list(2): Getting info of entry 6 (11 available)...
0.458270 gphoto2-camera(2): Setting port info for port 'Universal Serial Bus' at 'usb:'...
0.458909 gphoto2-port(2): Setting timeout to 5000 millisecond(s)...
0.458929 gphoto2-port(2): Setting settings...
0.458941 libusb(2): gp_port_usb_update(old int=0, conf=-1, alt=-1), (new int=0, conf=-1, alt=-1)
0.458953 gphoto2-setting(2): Setting key 'port' to value 'usb:' (gphoto2)
0.458965 gphoto2-setting(2): Saving 2 setting(s) to file "/home/heart/.gphoto/settings"
0.459211 gphoto2-camera(2): Listing files in '/'...
0.459228 gphoto2-camera(2): Initializing camera...
0.459257 gphoto2-port(0): Could not find USB device (vendor 0x4a9, product 0x3110). Make sure this device is connected to the computer.
**0.459278 context(0): An error occurred in the io-library ('Bad parameters'): Could not find USB device (vendor 0x4a9, product 0x3110). Make sure this device is connected to the computer.**
```

---

### Post by sdennie on 2008-06-06
This would seem completely unrelated but, "gphoto" seems like it would be an X app to me.  Are you certain that the DISPLAY variable is set correctly when running the script.  It doesn't seem likely this problem would produce that exact error but, it's something to think about.  

The environment in general may not be setup right either.  You may be able to su login to the user you want to execute your scripts from the udev rule.

---

### Post by unutbu on 2008-06-06
Yes, I agree that there might be something wrong with my env -- I know they look quite different when I run the script via udev versus when I run it manually. (.dl-pictures-executed looks quite different). However, I don't know the right command(s) to force the udev env to look like my regular env...

I'm already using "su heart -c" to run the script via udev. Is there something else I need to do?

gphoto2 (despite its name) is a command-line program. It can be interactive if you don't use the --force-overwrite flag. Other than that, I think it can run fine in scripts.

Edit: This is the output of `env` when gphoto2 failed to download pictures:

```

DEVTYPE=usb_device
SHELL=/bin/bash
SUBSYSTEM=usb
OLDPWD=/
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb4/4-3
USER=heart
DEVNUM=028
MINOR=411
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
MAIL=/var/mail/heart
ACTION=add
UDEV_LOG=3
PWD=/home/heart/images/XTi
BUSNUM=004
LANG=en_US.UTF-8
MAJOR=189
UDEVD_EVENT=1
DEVNAME=/dev/4-3
HOME=/home/heart
SHLVL=2
DEVICE=/proc/bus/usb/004/028
LOGNAME=heart
PRODUCT=4a9/3110/2
TYPE=0/0/0
PHYSDEVBUS=usb
SEQNUM=3343
_=/usr/bin/env

```

This is `env` when gphoto2 was run manually:
```

SSH_AGENT_PID=6000
TERM=dumb
SHELL=/bin/bash
XDG_SESSION_COOKIE=9f3ee39221cbea3193969a0047912100-1212775972.121845-1952516981
FVWM_USERDIR=/home/heart/.fvwm
HOSTDISPLAY=tack:0.0
fvwm_term=/usr/bin/gnome-terminal
GTK_RC_FILES=/etc/gtk/gtkrc:/home/heart/.gtkrc-1.2-gnome2
OLDPWD=/home/heart/images/XTi
EMACS=t
USER=heart
fvwm_webbrowser=/usr/bin/firefox
TERMCAP=
GNOME_KEYRING_SOCKET=/tmp/keyring-clBBOb/socket
SSH_AUTH_SOCK=/tmp/ssh-CBolgK5938/agent.5938
SESSION_MANAGER=local/tack:/tmp/.ICE-unix/5938
fvwm_video_player=/usr/bin/mplayer
COLUMNS=90
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/heart/bin:/home/heart/pybin
DESKTOP_SESSION=default
GDM_XSERVER_LOCATION=local
PWD=/home/heart/images/XTi
TEX=/usr/bin/latex
GNOME_KEYRING_PID=5935
LANG=en_US.UTF-8
GDM_LANG=en_US.UTF-8
PSRESOURCEPATH=/usr/X11R6/lib/X11/fonts/100dpi
fvwm_media_player=/usr/bin/xmms
GDMSESSION=default
HISTCONTROL=ignoreboth
TEXINPUTS=.:/home/heart/texmf:/home/heart/tex:/home/heart/tex/AIM_authorpackage/:
SHLVL=2
HOME=/home/heart
GNOME_DESKTOP_SESSION_ID=Default
BASH_ENV=/home/heart/.bashrc
LOGNAME=heart
XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-byWo4W8Kc2,guid=72265671cef94a68ee8c8c0048497e26
LESSOPEN=| /usr/bin/lesspipe %s
FVWM_MODULEDIR=/usr/lib/fvwm/2.5.21
WINDOWPATH=7
DISPLAY=:0.0
INSIDE_EMACS=23.0.60.1,comint
LESSCLOSE=/usr/bin/lesspipe %s %s
XAUTHORITY=/home/heart/.Xauthority
_=/usr/bin/env

```

---

### Post by mc4man on 2008-06-06
@ unutbu
did you end up calling script directly from the auto import?
I'm using gphoto2 also (w/exif) and it works perfectly that way. 
I was thinking this was an exercise writing rules so i bit my tongue so to speak.

---

### Post by unutbu on 2008-06-06
I don't know about auto import. Please explain.

It is true I'm using this problem mainly as a way to learn about udev, but I wouldn't mind learning about auto import too.

Is auto import the same as System>Preferences>Removeable Drives and Media?

---

### Post by mc4man on 2008-06-07
What I did is put my script in home dir. I assume you did a chmod u+x on it.
Then in system -> preferences -> removable drives and media -> camera,  ck. import digital photographs. In the command box put in ./scriptname
for example mine - ```
./pictures.sh
```
i'd remove the ...rules lines you created
.....................................................................
When I turn on the camera the script silently runs and downloads the photos to Pictures. (the script i'm using reads the time,date stamp and creates sub dir. in Pictures based on that. For ex. 2008-06-06 is created and all photos from yesterday are dl to that folder, ect.

---

### Post by unutbu on 2008-06-07
Okay, thanks for that. In practice that is probably the easiest way, but I'm having fun learning about udev so I'm going to continue searching for a udev way.

I feel if I can crack this env problem, I might also learn why cron jobs are sometimes difficult to get running too...

---

### Post by unutbu on 2008-06-08
Here is another manifestation of the problem:

When I run `lsusb` from the CLI, I get
```
09:58:43 heart@tack:~% lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:2003 Dell Computer Corp. 
Bus 002 Device 002: ID 0461:4d15 Primax Electronics, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
**Bus 004 Device 007: ID 04a9:3110 Canon, Inc.** 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 07d1:3a08 D-Link System 
Bus 003 Device 001: ID 0000:0000  
```

But when I add

```
lsusb > /home/heart/images/XTi/lsusb.out
```

to the dl-pictures.sh script, I get 

```
10:02:08 heart@tack:~% cat /home/heart/images/XTi/lsusb.out
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:2003 Dell Computer Corp. 
Bus 002 Device 002: ID 0461:4d15 Primax Electronics, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 07d1:3a08 D-Link System 
Bus 003 Device 001: ID 0000:0000  
```

Is there some command I need to run so that the script can see the camera as a USB device?

---

### Post by fragos on 2008-06-08
I've two TV cards and a webcam which got mounted with different /dev/video{#} mount points for each boot. I created 95-perso.rules as follows and all is well with fixed mount points for each device:

KERNEL=="video*", SYSFS{vendor}=="0x4444", SYSFS{device}=="0x0016", SYSFS{name}=="ivtv0 encoder MPEG", SYMLINK+="video/pvr150"
KERNEL=="video*", SYSFS{vendor}=="0x109e", SYSFS{device}=="0x036e", SYMLINK+="video/bttv"
KERNEL=="video*", SYSFS{vendor}=="0x046d", SYSFS{device}=="0x092e", SYMLINK+="video/webcam"

---

### Post by unutbu on 2008-06-08
Thanks fragos. 

I just added SYMLINK+="camera" to any entry in
/etc/udev/rules.d/45-libgphoto2.rules:

```
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="3110", MODE="0660", GROUP="plugdev", SYMLINK+="camera"
```

This gives me an entry in /dev:
```
  lrwxrwxrwx  1 root   root          15 2008-06-08 16:13 camera -> bus/usb/008/003
```

When I turn on the camera, the dl-pictures.sh script runs, but I get the same error:

```
0.599959 context(0): An error occurred in the io-library ('Bad parameters'): Could not find USB device (vendor 0x4a9, product 0x3110). Make sure this device is connected to the computer.
```

I tried to use the symlink this way:

```

16:15:43 heart@tack:~% sudo mount /dev/camera /media/test/
mount: /dev/bus/usb/008/003 is not a block device

```

I don't understand udev very well, but I believe I have a camera that can not be mounted.
From /usr/share/doc/udev/writing_udev_rules/index.html#example-camera
I read

> Not all cameras work in this way: some of them use a non-storage protocol such as cameras supported by gphoto2. In the gphoto case, you do not want to be writing rules for your device, as is it controlled purely through userspace (rather than a specific kernel driver).

After reading that I was almost ready to give up on using udev to auto-download pictures, but while screwing around I discovered I could get udev to execute a script when the camera was turned on, so I figured I could actually use udev to auto-download pictures despite the above quote. Things have proven rather difficult since that point.

udev detects the camera, but for some reason gphoto2 seems to have trouble doing the same. The odd part is, gphoto2 works if I execute the same command from the CLI.
```

/usr/bin/gphoto2 --port usb: --force-overwrite --get-all-files
```

---

### Post by unutbu on 2008-06-12
Following mc4man's suggestion, I can successfully run dl-pictures.sh automatically via System>Preferences>Removable Drives and Media.

So the script can work when run from a non-interactive shell, but for some reason, it fails when run from udev rules. 

Any idea why this might happen?

---

