---
title: "running slow"
date: 2007-08-25
forum: General Help
---

### Post by alsehendo34 on 2007-08-25
apps seem to take a long time starting up any thing weird running here?

hendo@hendo:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
   30 ?        00:00:00 kblockd/0
   31 ?        00:00:00 kacpid
   32 ?        00:00:00 kacpi_notify
  121 ?        00:00:00 kseriod
  140 ?        00:00:00 pdflush
  141 ?        00:00:03 pdflush
  142 ?        00:00:00 kswapd0
  143 ?        00:00:00 aio/0
  324 ?        00:00:20 cupsd
 2007 ?        00:00:00 khpsbpkt
 2022 ?        00:00:00 knodemgrd_0
 2024 ?        00:00:00 ksuspend_usbd
 2025 ?        00:00:00 khubd
 2048 ?        00:00:00 ata/0
 2049 ?        00:00:00 ata_aux
 2380 ?        00:00:00 reiserfs/0
 2579 ?        00:00:00 udevd
 3546 ?        00:00:00 tifm/0
 3563 ?        00:00:00 pccardd
 3567 ?        00:00:00 kpsmoused
 3705 ?        00:00:00 kmmcd
 3889 ?        00:00:00 ntos_wq/0
 3890 ?        00:00:00 ndis_wq
 3891 ?        00:00:00 wrapndis_wq/0
 4065 ?        00:00:00 mount.ntfs-3g
 4253 tty4     00:00:00 getty
 4254 tty5     00:00:00 getty
 4258 tty2     00:00:00 getty
 4259 tty3     00:00:00 getty
 4260 tty1     00:00:00 getty
 4261 tty6     00:00:00 getty
 4530 ?        00:00:00 acpid
 4635 ?        00:00:00 syslogd
 4642 ?        00:00:00 avahi-autoipd
 4643 ?        00:00:00 avahi-autoipd
 4647 ?        00:00:00 dhclient3
 4722 ?        00:00:00 dd
 4724 ?        00:00:00 klogd
 4745 ?        00:00:33 dbus-daemon
 4761 ?        00:00:18 hald
 4762 ?        00:00:00 hald-runner
 4768 ?        00:00:00 hald-addon-keyb
 4769 ?        00:00:00 hald-addon-keyb
 4770 ?        00:00:00 hald-addon-keyb
 4771 ?        00:00:00 hald-addon-keyb
 4775 ?        00:00:00 hald-addon-acpi
 4776 ?        00:00:00 hald-addon-keyb
 4790 ?        00:00:24 hald-addon-stor
 4803 ?        00:00:00 dhcdbd
 4818 ?        00:00:00 NetworkManager
 4836 ?        00:00:00 avahi-daemon
 4837 ?        00:00:00 avahi-daemon
 4853 ?        00:00:00 NetworkManagerD
 4866 ?        00:00:00 system-tools-ba
 4867 ?        00:00:00 dbus-daemon
 4890 ?        00:00:00 gdm
 4891 ?        00:00:00 gdm
 4911 tty7     00:16:02 Xorg
 4963 ?        00:00:00 x-session-manag
 5007 ?        00:00:00 ssh-agent
 5010 ?        00:00:00 dbus-launch
 5011 ?        00:00:01 dbus-daemon
 5013 ?        00:00:00 gconfd-2
 5016 ?        00:00:00 gnome-keyring-d
 5018 ?        00:00:07 gnome-settings-
 5025 ?        00:00:00 sh
 5026 ?        00:00:00 esd
 5035 ?        00:00:34 gnome-panel
 5039 ?        00:00:20 nautilus
 5043 ?        00:00:50 gnome-screensav
 5045 ?        00:00:00 bonobo-activati
 5052 ?        00:00:00 gnome-vfs-daemo
 5056 ?        00:00:00 trashapplet
 5070 ?        00:00:04 mixer_applet2
 5095 ?        00:00:00 hpiod
 5098 ?        00:00:00 python
 5142 ?        00:00:00 atieventsd
 5164 ?        00:00:00 hald-addon-keyb
 5170 ?        00:00:00 hald-addon-keyb
 5248 ?        00:00:00 master
 5250 ?        00:00:00 qmgr
 5309 ?        00:00:00 hcid
 5328 ?        00:00:00 krfcommd
 5362 ?        00:00:00 atd
 5376 ?        00:00:00 cron
 5499 ?        00:00:00 mapping-daemon
 5506 ?        00:00:02 gnome-volume-ma
 5514 ?        00:00:01 update-notifier
 5517 ?        00:00:09 nm-applet
 5529 ?        00:01:06 gnome-cups-icon
 5531 ?        00:00:28 gnome-power-man
24866 ?        00:00:00 pickup
25736 ?        00:00:00 metacity
25748 ?        00:00:00 gnome-terminal
25763 ?        00:00:00 gnome-pty-helpe
25764 pts/0    00:00:00 bash
25791 pts/0    00:00:00 ps
32615 ?        00:00:01 artsd

---

### Post by K.Mandla on 2007-08-26
Everything looks kosher. What kind of hardware are you using? This looks like a full Gnome installation. How fast is the processor on this machine, and how much memory does it have?

---

### Post by alsehendo34 on 2007-08-26
2.8GHz P4 Sony Vio Laptop PCG-K23 512M Ram

Running Ubuntu Studio

ATI driver on 345m radion--3D works--runs same speed for basic things with vesa

altos wifi running under ndiswrapper--only way it would work!
It seems things may have slowed up after this was done? 

Takes 20-30 seconds to load applications like terminal and firefox--is this normal? :-({|=

Do I need more Ram for ubuntu?

Any other ideas

---

### Post by K.Mandla on 2007-08-26
A couple, but they all involve some experimentation. I'd suggest backing up anything important before going on.

Usually Gnome (the desktop environment for Ubuntu) is rather heavyweight. What you describe is unacceptable though. You might try a different desktop system -- install [kubuntu-desktop]("http://packages.ubuntu.com/feisty/metapackages/kubuntu-desktop") or even [xubuntu-desktop]("http://packages.ubuntu.com/feisty/metapackages/xubuntu-desktop") -- and see if you get better response times with those.

You could also strip down your system to bare essentials and see if there's anything in particular that is causing problems. There are some good ideas in the wiki. [uwiki]Installation/LowMemorySystems[/uwiki]

If it's hardware related, you might find error messages or reports inside the log folder, which (I think) is inside /var/log, or somewhere near that (I'm using Arch right now, and I have removed system logging, so I can't find it :roll: ). There should be a kernel.log and perhaps a couple of others; scan those to see if anything jumps out at you.

Aside from that, 512Mb should be plenty to run Ubuntu, provided you're not doing heavyweight rendering or high-end gaming. I wouldn't suggest spending more money on your computer until you can figure out what's slowing you down.

---

### Post by mguitar on 2007-08-29
I have the same laptop, Sony pcg-k23, and have been struggling for the last week trying to get the wifi working in feisty. I have tried ndiswrapper with multiple drivers (including the one from sony's website and some from the ndiswrapper website) to no avail. Exactly what driver did you use and are there any tricks to getting it to work? I'd be willing to use ubuntustudio if necessary.  Thanks.

---

