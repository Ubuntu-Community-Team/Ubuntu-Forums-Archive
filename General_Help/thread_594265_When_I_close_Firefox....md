---
title: "When I close Firefox..."
date: 2007-10-27
forum: General Help
---

### Post by scuba_suit on 2007-10-27
i can't open it up again. a message screen saying that it can't open another one until i close firefox because it's still running (eventhough it's not there on the screen or minimized), i basically have to restart the computer again to open firefox again. what can i do?

---

### Post by taurus on 2007-10-27
Can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ps -A
```

---

### Post by scuba_suit on 2007-10-27
here's what came up:


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
   96 ?        00:00:00 kseriod
  117 ?        00:00:00 pdflush
  118 ?        00:00:00 pdflush
  119 ?        00:00:00 kswapd0
  120 ?        00:00:00 aio/0
 2121 ?        00:00:00 ksuspend_usbd
 2122 ?        00:00:00 khubd
 2176 ?        00:00:00 ata/0
 2177 ?        00:00:00 ata_aux
 2179 ?        00:00:00 scsi_eh_0
 2180 ?        00:00:00 scsi_eh_1
 2451 ?        00:00:00 kjournald
 2650 ?        00:00:00 udevd
 3494 ?        00:00:00 kpsmoused
 3943 ?        00:00:00 portmap
 4071 tty4     00:00:00 getty
 4072 tty5     00:00:00 getty
 4077 tty2     00:00:00 getty
 4078 tty3     00:00:00 getty
 4079 tty1     00:00:00 getty
 4080 tty6     00:00:00 getty
 4321 ?        00:00:00 acpid
 4427 ?        00:00:00 syslogd
 4481 ?        00:00:00 dd
 4483 ?        00:00:00 klogd
 4504 ?        00:00:00 dbus-daemon
 4520 ?        00:00:01 hald
 4521 ?        00:00:00 hald-runner
 4527 ?        00:00:00 hald-addon-acpi
 4535 ?        00:00:00 hald-addon-keyb
 4544 ?        00:00:00 hald-addon-keyb
 4547 ?        00:00:00 hald-addon-keyb
 4559 ?        00:00:00 hald-addon-stor
 4572 ?        00:00:00 dhcdbd
 4587 ?        00:00:00 NetworkManager
 4608 ?        00:00:00 avahi-daemon
 4609 ?        00:00:00 avahi-daemon
 4622 ?        00:00:00 NetworkManagerD
 4635 ?        00:00:00 system-tools-ba
 4643 ?        00:00:00 dbus-daemon
 4659 ?        00:00:00 gdm
 4660 ?        00:00:00 gdm
 4694 tty7     00:01:48 Xorg
 4747 ?        00:00:00 cupsd
 4777 ?        00:00:00 hpiod
 4780 ?        00:00:00 python
 4893 ?        00:00:00 lockd
 4894 ?        00:00:00 rpciod/0
 4895 ?        00:00:00 nfsd4
 4896 ?        00:00:00 nfsd
 4897 ?        00:00:00 nfsd
 4898 ?        00:00:00 nfsd
 4899 ?        00:00:00 nfsd
 4900 ?        00:00:00 nfsd
 4901 ?        00:00:00 nfsd
 4902 ?        00:00:00 nfsd
 4903 ?        00:00:00 nfsd
 4907 ?        00:00:00 rpc.mountd
 4931 ?        00:00:00 inetd
 4967 ?        00:00:00 dhclient
 4972 ?        00:00:00 nmbd
 4974 ?        00:00:00 smbd
 5006 ?        00:00:00 smbd
 5013 ?        00:00:00 sshd
 5069 ?        00:00:00 rpc.statd
 5079 ?        00:00:00 rpc.idmapd
 5096 ?        00:00:00 hcid
 5114 ?        00:00:00 krfcommd
 5172 ?        00:00:00 atd
 5186 ?        00:00:00 cron
 5326 ?        00:00:00 x-session-manag
 5365 ?        00:00:00 ssh-agent
 5368 ?        00:00:00 dbus-launch
 5369 ?        00:00:00 dbus-daemon
 5371 ?        00:00:00 gconfd-2
 5374 ?        00:00:00 gnome-keyring-d
 5376 ?        00:00:00 gnome-settings-
 5383 ?        00:00:00 sh
 5384 ?        00:00:00 esd
 5388 ?        00:00:00 compiz
 5391 ?        00:00:01 gnome-panel
 5392 ?        00:00:00 nautilus
 5397 ?        00:00:00 gtk-window-deco
 5401 ?        00:00:00 bonobo-activati
 5404 ?        00:00:01 compiz.real
 5405 ?        00:00:00 gnome-volume-ma
 5407 ?        00:00:00 gnome-vfs-daemo
 5411 ?        00:00:00 update-notifier
 5417 ?        00:00:00 evolution-alarm
 5419 ?        00:00:00 nm-applet
 5423 ?        00:00:00 mapping-daemon
 5427 ?        00:00:00 gnome-cups-icon
 5432 ?        00:00:00 gnome-power-man
 5434 ?        00:00:00 trashapplet
 5474 ?        00:00:00 mixer_applet2
 5482 ?        00:00:00 notification-da
 5487 ?        00:00:00 gnome-screensav
 6442 ?        00:00:04 firefox-bin
 6497 ?        00:00:00 gnome-terminal
 6501 ?        00:00:00 gnome-pty-helpe
 6502 pts/0    00:00:00 bash
 6525 pts/0    00:00:00 ps

---

### Post by taurus on 2007-10-27
You still have it running in the background.

```
**6442 ? 00:00:04 firefox-bin**
```
So, you can kill it before you open another one with

```
sudo kill -9 6442
```

---

### Post by scuba_suit on 2007-10-27
everytime that happens i just put that line in the terminal? hey i'm new to linux, is there a ctrl-alt-delete window that pops up to show what's running? or is it just that ps -A code?

---

### Post by taurus on 2007-10-27
The PID (process ID, the first set of number) won't be the same so if you want to use the command about to kill it, you need to know the exact PID.  You can see what with the **ps -A** output.

---

### Post by scuba_suit on 2007-10-27
cool, after the ps -A, get the PID number then sudo kill -9 (PID #), right? that -9 doesn't change...

---

### Post by osx424242 on 2007-10-27
Right, that -9 won't change.  You can use 'grep' to narrow the list, too:
```
ps -A | grep firefox
```
The "|" says, take all the output from the first command and 'pipe' it to the second command.  'grep' says, look for lines that match this text and only output them (i.e. don't print out any other lines).  grep also takes a '-i' option to ignore case, that will probably come in handy for you in the future (e.g. "ps -A | grep -i progName").

---

### Post by scuba_suit on 2007-10-27
that line is that the shift forward slash key?

---

### Post by taurus on 2007-10-27
Yes.  It's called pipe.

---

### Post by kostkon on 2007-10-27
You can just go to *System -> Administration -> System Monitor* and kill it from there. But this is not a solution to your problem. I suspect that an extension is causing this. Did you install any extensions in *Firefox*? Try to remove any extension that you feel it may cause this.

In any case, you can try to create a new profile and use it to see if this problem happens again.

Go to terminal and run *Firefox* like this
```
firefox -profilemanager
```

More information about the *Profile Manager* and about managing profiles in general you can find [here]("http://www.mozilla.org/support/firefox/profile").

---

