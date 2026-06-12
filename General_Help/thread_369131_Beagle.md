---
title: "Beagle?"
date: 2007-02-24
forum: General Help
---

### Post by HessiaNerd on 2007-02-24
I want to start off by saying the community here has been great so far.  I have been very impressed at how helpful yall have been and I hope you can help me with my next question even though it is somewhat vague.

BEAGLE?

So I was having trouble with Nautilus' search functionality (i.e. not working at ALL)  and I ran against this thread:
[http://www.ubuntuforums.org/showthread.php?t=346672](http://www.ubuntuforums.org/showthread.php?t=346672)

allwin was nice enough to post this seemingly helpful remark:
> **allwin said:**
> 
Uninstall the BEAGLE package, unless you know you have specific need for Beagle!
.... Worked for me.

I was curious to see what BEAGLE even was:
[http://beagle-project.org/Main_Page](http://beagle-project.org/Main_Page)
and I gotta say, it looks pretty cool...

its not running on my box as far as I can tell (ps -A):
```
ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 migration/1
    6 ?        00:00:00 ksoftirqd/1
    7 ?        00:00:00 watchdog/1
    8 ?        00:00:00 events/0
    9 ?        00:00:00 events/1
   10 ?        00:00:00 khelper
   11 ?        00:00:00 kthread
   14 ?        00:00:00 kblockd/0
   15 ?        00:00:00 kblockd/1
   16 ?        00:00:00 kacpid
   17 ?        00:00:00 kacpi_notify
  106 ?        00:00:00 kseriod
  139 ?        00:00:00 pdflush
  140 ?        00:00:00 pdflush
  141 ?        00:00:01 kswapd0
  142 ?        00:00:00 aio/0
  143 ?        00:00:00 aio/1
  767 ?        00:00:00 kirqd
 1739 ?        00:00:00 ata/0
 1740 ?        00:00:00 ata/1
 1744 ?        00:00:00 scsi_eh_0
 1745 ?        00:00:00 scsi_eh_1
 1811 ?        00:00:00 khubd
 1842 ?        00:00:00 khpsbpkt
 1877 ?        00:00:00 knodemgrd_0
 1921 ?        00:00:00 kjournald
 2007 ?        00:00:00 logd
 2136 ?        00:00:00 udevd
 2954 ?        00:00:00 shpchpd
 3047 ?        00:00:00 kpsmoused
 3130 ?        00:00:00 kgameportd
 3608 ?        00:00:00 dhclient3
 3846 tty1     00:00:00 getty
 3847 tty2     00:00:00 getty
 3848 tty3     00:00:00 getty
 3849 tty4     00:00:00 getty
 3850 tty5     00:00:00 getty
 3851 tty6     00:00:00 getty
 4080 ?        00:00:00 acpid
 4214 ?        00:00:00 dd
 4216 ?        00:00:00 klogd
 4290 ?        00:00:00 gdm
 4307 ?        00:00:16 gdm
 4315 tty7     00:27:30 Xorg
 4345 ?        00:00:00 hpiod
 4348 ?        00:00:00 python
 4401 ?        00:00:00 dbus-daemon
 4416 ?        00:00:02 hald
 4417 ?        00:00:00 hald-runner
 4425 ?        00:00:00 hald-addon-acpi
 4432 ?        00:00:00 hald-addon-usb-
 4438 ?        00:00:00 hald-addon-keyb
 4460 ?        00:00:29 hald-addon-stor
 4474 ?        00:00:00 perl
 4535 ?        00:00:00 hcid
 4539 ?        00:00:00 sdpd
 4558 ?        00:00:00 krfcommd
 4592 ?        00:00:00 atd
 4605 ?        00:00:00 cron
 4791 ?        00:00:00 cupsd
 4865 ?        00:00:00 x-session-manag
 4901 ?        00:00:00 ssh-agent
 4904 ?        00:00:00 dbus-launch
 4905 ?        00:00:00 dbus-daemon
 4907 ?        00:00:01 gconfd-2
 4910 ?        00:00:00 gnome-keyring-d
 4913 ?        00:00:10 gnome-settings-
 4924 ?        00:00:00 sh
 4925 ?        00:00:00 esd
 4935 ?        00:00:58 gnome-panel
 4937 ?        00:01:39 nautilus
 4941 ?        00:00:00 bonobo-activati
 4942 ?        00:00:00 gnome-volume-ma
 4949 ?        00:00:01 update-notifier
 4952 ?        00:00:00 gnome-vfs-daemo
 4964 ?        00:00:00 evolution-alarm
 4981 ?        00:00:00 gnome-cups-icon
 4983 ?        00:00:01 xbindkeys
 5035 ?        00:00:00 gnome-power-man
 5047 ?        00:01:26 emerald
 5073 ?        00:00:01 evolution-data-
 5091 ?        00:00:00 mapping-daemon
 5093 ?        00:00:02 mixer_applet2
 5156 ?        00:00:09 notification-da
 5166 ?        00:00:27 gnome-screensav
 6402 ?        00:00:00 kjournald
 6974 ?        00:14:54 beryl
28826 ?        00:00:00 syslogd
 3095 ?        00:10:28 firefox-bin
20818 ?        00:00:05 python
23781 ?        00:00:00 at-spi-registry
25407 ?        00:00:00 beryl-manager
25481 ?        00:00:17 gij-4.1
25824 ?        00:00:00 gnome-terminal
25827 ?        00:00:00 gnome-pty-helpe
25828 pts/0    00:00:00 bash
26678 pts/0    00:00:00 ps


```

but to be honest, I dont as of yet understand half of what is going on on that list..

So what do I do?  Do I install BEAGLE?
[http://www.ubuntuforums.org/showthread.php?t=364054&highlight=BEAGLE](http://www.ubuntuforums.org/showthread.php?t=364054&highlight=BEAGLE)

Will it take up too much process time?
[http://www.ubuntuforums.org/showthread.php?t=365604](http://www.ubuntuforums.org/showthread.php?t=365604)

I would be REALLY impressed if it searched EXIF data
[http://www.ubuntuforums.org/showthread.php?t=366349](http://www.ubuntuforums.org/showthread.php?t=366349)
but don't understand a word of the above post

I understand its a personal preference, but I would just like to be more informed.  Why doesn't Nautilus Search work.  Will it integrate if in install it (as far as I can tell the only thing installed on my system right now is the libbeagle0 'library for accessing beagle (development files)').  WHAT WILL GET ME DECENT SEARCH FUNCTIONALITY?

thanks for your help and advice.

---

### Post by Daveth on 2007-02-24
yes, type "beagle" into synaptic. It comes in 2 sorts (breeds!) 1 for gnome, 1 for kde. It indexes in the background. I doubt you will even notice it sniffing out your filesin the background. There is a nice plugin to index Evolution mail as well, finding contacts and messages.

---

### Post by cisforcojo on 2007-02-24
Beagle is the best search program I've found and it sits conveniently on the toolbar. Before beagle, I'd always have to use 'whereis' on the commandline.

---

