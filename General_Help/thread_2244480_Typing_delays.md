---
title: "Typing delays"
date: 2014-09-16
forum: General Help
---

### Post by Engineeringtech on 2014-09-16
I was running Ubuntu 12.04LTS on my 2004 laptop until a few weeks ago.    When it ran, it ran fine.   But when it was bad, I had numerous freezes and crashes.  So I formatted my drive and installed Lubuntu 13.10.     Lubuntu seemed quick for a week or so, then I started having a very bad problem with a couple applications.  I type, and there is a 1 1/2 to 2 second delay between hitting the key and seeing the character appear on the screen.   That is incredibly difficult to deal with.  As I am typing this on the same machine right this very moment, without seeing any delay, I can say with reasonable certainty that this is not a hardware problem.  Prior to creating this post (with Firefox), I created a short letter with AbiWord and it was TORTURE.  Nothing else was running at the time.   

Any ideas?

P.S.  I know Lubuntu 13.10 just fell off the support list.  I had burned an installation disk a few months ago without knowing this. ....I'd rather not install a new OS right now, if I don't have to.

---

### Post by tgalati4 on 2014-09-17
It's quite possible that a 10-year-old laptop has a hardware problem.  When was the last time you opened it up and cleaned it out and reseated the ribbon connectors?

If the heatsink is clogged, the CPU will get hot and it will automatically slow down to compensate--does that sound familiar?

Simply changing operating systems will not solve a hardware problem.

Of course, you could have a runaway process that is taking up your CPU and that will result in slow response.

Open a terminal and run *top* and see what is going on.  How much RAM do you have?

```
top
free
```

---

### Post by Engineeringtech on 2014-09-17
> **tgalati4 said:**
> It's quite possible that a 10-year-old laptop has a hardware problem.  When was the last time you opened it up and cleaned it out and reseated the ribbon connectors?

If the heatsink is clogged, the CPU will get hot and it will automatically slow down to compensate--does that sound familiar? Simply changing operating systems will not solve a hardware problem. Of course, you could have a runaway process that is taking up your CPU and that will result in slow response. Open a terminal and run *top* and see what is going on.  How much RAM do you have?

```
top
free
```


Thanks for your reply.  As I said in my post, this only affects a couple applications.  I can type just fine - in this window for instance.   I'm an electronic tech.  I disassembled my computer just a couple years ago, and checked everything, including the fan.   This is a triple boot system.  DOS, WIndows, and Ubuntu. DOS and Windows run fine.  No slowdowns.   I ran TOP and It shows 766.160 MB total RAM.  (I have two sticks, 512MB, and 128MB).  The free amount hovers between 150 and  76 MB.  Curiously, swap memory is 1563.816 MB and NONE of it is being used.  Is that normal?

---

### Post by vasa1 on 2014-09-17
> **Engineeringtech said:**
> ..., this only affects a couple applications. ...
Did you mention which applications those are? Abiword and ...?

---

### Post by HermanAB on 2014-09-18
It sounds like a hardware problem to me with the machine making infrequent read/write errors and gradually messing up the system.
a. Vacuum the machine and get all the lint out of the cooling system
b. You may have bad memory (RAM and disk drive), try to test it (tests usually won't find anything wrong though, since if the problem is so bad that the test will actually find something, then the machine usually won't run at all)

---

### Post by Engineeringtech on 2014-09-18
AbiWord.      SOMETIMES Firefox, but only at certain sites like Yahoo and Hotmail, when I am trying to compose a new message .  No problem whatsoever at this website..   I think Sylpheed did it too, when I was composing a message, but I can't seem to get a repeat performance.  AbiWord exhibits the typing delay every time I run it.   

My computer is clean.  No lint fouling it up.  The laptop runs reasonably cool.  Doesn't exhibit the problems when I run Windows.  I have run the Ubuntu memory tests offered at boot up time.  No problem found over an hour period.

---

### Post by HermanAB on 2014-09-18
OK, then install and run 'top' and 'ntop' to see what is chewing up system resources.

---

### Post by Engineeringtech on 2014-09-19
I installed NTOP with Synaptic Package Manager.   I opened a terminal, and started NTOP.  Error messages.   I started TOP.  Results extended beyond the height of the screen.   I tried to direct the output ot a text file with "TOP >Text.txt"   That resulted in gibberish.   Not liking Lubuntu right now, because I can't even do a screen capture.  Installed SCROT for screen capture, but I have to start it from a terminal window.  How do I do that, when the terminal window is locked up with the results of running TOP or NTOP?

---

### Post by vasa1 on 2014-09-19
```
top -bn1 > ~/Desktop/top-output
```
If you have pastebinit installed, run
```
top -bn1 | pastebinit
```and paste the link here in case of lengthy output.

---

### Post by vasa1 on 2014-09-19
> **Engineeringtech said:**
>  ... Not liking Lubuntu right now, because I can't even do a screen capture.  Installed SCROT for screen capture, but I have to start it from a terminal window.  ...
If you really have installed Lubuntu, you wouldn't need to install "SCROT". Scrot is installed by default in Lubuntu. 

Lubuntu works just fine for me. Like everything in this world, it isn't perfect; I'm not; I don't know about the rest.

---

### Post by Engineeringtech on 2014-09-20
Sorry for the delay.  I have been ill.     Thank you for the guidance with the TOP command.   I do not have a webpage to post the output, so I will post it here:

Sorry about that.

top - 17:46:50 up  2:55,  2 users,  load average: 0.05, 0.28, 0.49
Tasks: 114 total,   1 running, 113 sleeping,   0 stopped,   0 zombie
%Cpu(s): 41.0 us,  5.4 sy,  0.1 ni, 52.2 id,  1.0 wa,  0.0 hi,  0.3 si,  0.0 st
KiB Mem:    766160 total,   541712 used,   224448 free,    21640 buffers
KiB Swap:  1563816 total,     3432 used,  1560384 free,   170620 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND
 1391 jim       20   0 45800 3624 2684 S   6.0  0.5   0:25.34 ibus-daemon
 2648 jim       20   0  6456 1144  880 R   6.0  0.1   0:00.02 top
    1 root      20   0  4040 2084 1196 S   0.0  0.3   0:03.86 init
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S   0.0  0.0   0:01.38 ksoftirqd/0
    5 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kworker/0:0H
    7 root      rt   0     0    0    0 S   0.0  0.0   0:00.00 migration/0
    8 root      20   0     0    0    0 S   0.0  0.0   0:00.00 rcu_bh
    9 root      20   0     0    0    0 S   0.0  0.0   0:13.65 rcu_sched
   10 root      rt   0     0    0    0 S   0.0  0.0   0:00.15 watchdog/0
   11 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 khelper
   12 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kdevtmpfs
   13 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 netns
   14 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 writeback
   15 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kintegrityd
   16 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 bioset
   17 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 crypto
   18 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kworker/u3:0
   19 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kblockd
   20 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 ata_sff
   21 root      20   0     0    0    0 S   0.0  0.0   0:00.00 khubd
   22 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 md
   23 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 devfreq_wq
   25 root      20   0     0    0    0 S   0.0  0.0   0:00.00 khungtaskd
   26 root      20   0     0    0    0 S   0.0  0.0   0:00.38 kswapd0
   27 root      25   5     0    0    0 S   0.0  0.0   0:00.00 ksmd
   28 root      39  19     0    0    0 S   0.0  0.0   0:00.00 khugepaged
   29 root      20   0     0    0    0 S   0.0  0.0   0:00.00 fsnotify_mark
   30 root      20   0     0    0    0 S   0.0  0.0   0:00.00 ecryptfs-kthrea
   42 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kthrotld
   47 root      20   0     0    0    0 S   0.0  0.0   0:00.00 scsi_eh_0
   48 root      20   0     0    0    0 S   0.0  0.0   0:00.00 scsi_eh_1
   69 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 deferwq
   70 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 charger_manager
  116 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 firewire
  125 root      20   0     0    0    0 S   0.0  0.0   0:01.84 kjournald
  256 root      20   0  2904  520  448 S   0.0  0.1   0:00.96 upstart-udev-br
  269 root      20   0 11904  980  864 S   0.0  0.1   0:01.01 systemd-udevd
  347 messageb  20   0  4272 1688 1004 S   0.0  0.2   0:03.14 dbus-daemon
  364 root      20   0  4864 1136 1136 S   0.0  0.1   0:00.00 bluetoothd
  372 root      20   0  4040 1196 1132 S   0.0  0.2   0:00.03 systemd-logind
  375 syslog    20   0 30072  940  824 S   0.0  0.1   0:02.37 rsyslogd
  385 avahi     20   0  3492 1224 1144 S   0.0  0.2   0:00.05 avahi-daemon
  386 avahi     20   0  3492  204  192 S   0.0  0.0   0:00.00 avahi-daemon
  406 root      10 -10     0    0    0 S   0.0  0.0   0:00.00 krfcommd
  419 root      20   0  7852 1560 1560 S   0.0  0.2   0:00.36 cupsd
  423 root      20   0  3028  484  396 S   0.0  0.1   0:00.32 upstart-file-br
  425 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 kpsmoused
  431 root      20   0     0    0    0 S   0.0  0.0   0:00.00 pccardd
  435 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 ttm_swap
  458 root      20   0     0    0    0 S   0.0  0.0   0:00.00 pccardd
  471 root       0 -20     0    0    0 S   0.0  0.0   0:00.00 cfg80211
  488 root       0 -20     0    0    0 S   0.0  0.0   0:00.42 kworker/u3:1
  565 root      20   0  7624 2488 1860 S   0.0  0.3   0:00.18 modem-manager
  588 root      20   0 44136 5024 4048 S   0.0  0.7   0:05.25 NetworkManager
  606 root      20   0 34456 4220 2792 S   0.0  0.6   0:00.26 polkitd
  645 root      20   0  3016  628  344 S   0.0  0.1   0:00.26 upstart-socket-
  697 root      20   0  6700 1956 1556 S   0.0  0.3   0:00.47 wpa_supplicant
  805 root      20   0  4668  808  696 S   0.0  0.1   0:00.00 getty
  816 root      20   0  4668  816  696 S   0.0  0.1   0:00.00 getty
  832 root      20   0  4668  816  696 S   0.0  0.1   0:00.00 getty
  837 root      20   0  4668  824  696 S   0.0  0.1   0:00.00 getty
  840 root      20   0  4668  816  696 S   0.0  0.1   0:00.00 getty
  861 root      20   0  5536 2356  640 S   0.0  0.3   0:00.00 dhclient
  895 root      20   0  3168  928  724 S   0.0  0.1   0:00.01 cron
  908 ntop      20   0 88992 5512 1068 S   0.0  0.7   0:00.48 ntop
  909 whoopsie  20   0 52048 4084 3180 S   0.0  0.5   0:00.05 whoopsie
  925 root      20   0 33964 2952 2428 S   0.0  0.4   0:00.08 lightdm
  980 root      20   0 87112  35m  10m S   0.0  4.8   9:11.56 Xorg
 1055 root      20   0  4668  816  696 S   0.0  0.1   0:00.00 getty
 1066 root      20   0 34608 3432 2792 S   0.0  0.4   0:00.46 accounts-daemon
 1083 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kauditd
 1137 nobody    20   0  6760 1320 1108 S   0.0  0.2   0:03.67 dnsmasq
 1179 root      20   0 17360 3180 2584 S   0.0  0.4   0:00.25 lightdm
 1331 jim       20   0  6716 1728 1312 S   0.0  0.2   0:00.64 init
 1378 jim       20   0  4148  204    0 S   0.0  0.0   0:00.00 ssh-agent
 1382 jim       20   0  4352 1420  824 S   0.0  0.2   0:00.25 dbus-daemon
 1387 jim       20   0  6152 1048  912 S   0.0  0.1   0:00.33 upstart-event-b
 1403 jim       20   0 50056 6228 5004 S   0.0  0.8   0:00.25 lxsession
 1408 jim       20   0 28880 2568 2184 S   0.0  0.3   0:00.06 gvfsd
 1409 jim       20   0  6156  368  192 S   0.0  0.0   0:00.16 upstart-dbus-br
 1414 jim       20   0  6436  648  408 S   0.0  0.1   0:00.06 upstart-file-br
 1416 jim       20   0  6156  376  192 S   0.0  0.0   0:00.46 upstart-dbus-br
 1420 jim       20   0 41700 2492 2132 S   0.0  0.3   0:00.03 gvfsd-fuse
 1424 jim       20   0 36784 2944 2568 S   0.0  0.4   0:00.05 ibus-dconf
 1425 jim       20   0  110m  10m 7512 S   0.0  1.4   0:07.63 ibus-ui-gtk3
 1429 jim       20   0 40928 5748 4700 S   0.0  0.8   0:09.30 ibus-x11
 1436 jim       20   0 42344 2844 2420 S   0.0  0.4   0:00.02 at-spi-bus-laun
 1440 jim       20   0  3676 1576 1292 S   0.0  0.2   0:00.05 dbus-daemon
 1443 jim       20   0 17288 3004 2572 S   0.0  0.4   0:00.18 at-spi2-registr
 1456 jim       20   0 34348 9.8m 6824 S   0.0  1.3   0:04.32 openbox
 1458 jim       20   0  122m  13m   9m S   0.0  1.9   0:24.82 lxpanel
 1460 jim       20   0  191m  14m  10m S   0.0  1.9   0:02.68 nm-applet
 1462 jim       20   0  159m  16m  13m S   0.0  2.3   0:00.82 pcmanfm
 1466 jim       20   0 28516 2820 2472 S   0.0  0.4   0:06.50 ibus-engine-sim
 1477 jim       20   0 25040 2708 2328 S   0.0  0.4   0:00.02 menu-cached
 1483 jim       20   0 38236 4032 3124 S   0.0  0.5   0:00.23 gvfs-udisks2-vo
 1486 root      20   0 50944 4684 3240 S   0.0  0.6   0:05.94 udisksd
 1507 jim       20   0 27776 2360 2012 S   0.0  0.3   0:00.01 gvfs-mtp-volume
 1519 jim       20   0 28880 2560 2112 S   0.0  0.3   0:00.02 gvfs-gphoto2-vo
 1530 ntp       20   0  5744 1764 1340 S   0.0  0.2   0:01.27 ntpd
 1537 jim       20   0 39328 2536 2120 S   0.0  0.3   0:00.02 gvfs-afc-volume
 1543 jim       20   0 10080 2196 1836 S   0.0  0.3   0:00.05 gconfd-2
 1552 jim       20   0  787m 213m  40m S   0.0 28.5  69:31.49 firefox
 1891 root      20   0 32924  13m 6028 S   0.0  1.8   0:00.83 python3
 2364 root      20   0     0    0    0 S   0.0  0.0   0:01.40 kworker/0:2
 2522 root      20   0     0    0    0 S   0.0  0.0   0:00.20 kworker/u2:2
 2552 root      20   0     0    0    0 S   0.0  0.0   0:00.38 kworker/u2:0
 2554 root      20   0     0    0    0 S   0.0  0.0   0:00.18 kworker/0:0
 2587 root      20   0     0    0    0 S   0.0  0.0   0:00.04 kworker/0:1
 2592 jim       20   0  112m  12m 9604 S   0.0  1.6   0:00.82 x-terminal-emul
 2593 root      20   0     0    0    0 S   0.0  0.0   0:00.04 kworker/u2:1
 2594 jim       20   0  2440  704  580 S   0.0  0.1   0:00.00 gnome-pty-helpe
 2595 jim       20   0  7376 2428 1560 S   0.0  0.3   0:00.17 bash

---

### Post by Engineeringtech on 2014-09-23
Just to re-iterate, I am seeing very long typing delays, and a deformed, flaky cursor when I use Abiword, the only word processor installed in Lubuntu.   Makes it just about impossible to type a letter.  So other than toss out my hardware, does anyone here have any idea how to fix this?  Obviously it is s software problem.  I have no problem whatsoever typing in this window.  No delays, or wierd looking cursors.   I installed another text editor, Pico, and I can type just fine with it.  But it runs from a terminal window, and I don't know how to save / open files on my desktop or data partition, from the terminal window..    I uninstalled Abiword, and reinstalled.  That made no difference.  I opened the Synaptic Package Manager and looked for another word processor to install, but couldn't find one.

---

### Post by vasa1 on 2014-09-23
As I asked before ... is this a pure Lubuntu installation or have you modified it in some way? Why did you need to install scrot when scrot *should* be present by default? Why do you have "firewire" in your top output?

Note that you have had problems before with this machine which is why you installed Lubuntu. So, even though you're confident it's a software issue, it may not be so.

---

### Post by Dennis N on 2014-09-23
> I uninstalled Abiword, and reinstalled. That made no difference. I opened the Synaptic Package Manager and looked for another word processor to install, but couldn't find one. 
LibreOffice Writer is one suggestion for a good word processor.

---

### Post by vasa1 on 2014-09-23
@Dennis N, please look at OP's top output. I feel there are quite a few odd things about it. I doubt OP has a vanilla Lubuntu installed. Also, the %CPU in the summary is high and swap is being used, AFAICT. I very much doubt OP's issues are purely Abiword-related.

---

### Post by tgalati4 on 2014-09-23
Look through your log files for errors.

```
more /var/log/syslog
```

Check your harddisk's SMART status.

```
sudo smartctl -a /dev/sda
```

---

### Post by Engineeringtech on 2014-09-27
VASA1, I'm sorry if you are  offended that I haven't surrendered to your belief that this is a hardware problem.  You forget I already mentioned that my machine is dual boot and runs Windows without problems (typing delays).   I know my machine is old, but Lubuntu is made for older, lower powered hardware, is it not?     My machine was partitioned separately for Windows 2K and Ubuntu years ago, by an experienced Linux user.   It was only when I started having big problems with Ubuntu 12.04LTS, that I installed Lubuntu 13.10.     (I formatted the partition that Ubuntu 12.04 was on, and installed Lubuntu 13.10.)   Grub allows me to boot into either operating system (Windows or Lubuntu).  

You accuse me of having a non-standard Lubuntu installation because I have firewire!    My machine, a Gateway 600YGR laptop came with a firewire port as standard equipment.  The Lubuntu  installer configured the driver.    I don't know why you think I am concealing anything from you, just because I installed SCROT.     I believe you or someone else here asked to see the output of TOP.      TOP runs from a terminal window and I didn't know how to re-direct the output to a text file.   I tried to make a screenshot, but it didn't work.   So I used the Synaptic Package manager to install SCROT  

 VASA1 you've also expressed doubts that I have the issue with AbiWord alone.      I have to wonder... Do you think I am lying, or have some ulterior motive?   I have enough problems with my health and limited time at the computer, that it makes no sense to waste time at this forum.     I apologize if my posts are intermittent.   It is because of my limited access. 

I came up with a stopgap solution.  I write my letters and notes in a Sylpheed (email) compose window.  I can cut and paste the text into AbiWord, and save it as a text, RTF, etc. file.     I just can't type in AbiWord without the lengthy typing delays.   I'd love to use LibreOffice Writer, but it doesn't appear as an installable application in Synaptic Package Manager.  I have no experience with other methods of installing applications.

TGALATI4  - I thank you for your suggestions.  Right now I am dealing with chronic health problems.  Please give me a couple days to try them and get back to you.

---

### Post by The Cog on 2014-09-27
Calm down. OP is short for Original Poster, meaning the person who started the thread. Vasa1 is trying to help - we all are.

I have never heard of abiword specifically having this type of problem, so I do wonder if there is some kind of interaction between Abiword and your specific graphics drivers. 

If you want to try LibreOffice, the specific package is **libreoffice-writer** but I think you may as well install just package **libreoffice** which will also install the other libreoffice applications. Both will pull in a lot of dependency packages. You will find that LO is noticeably slower than abiword starting up, but I think it is quite usable once started.

---

### Post by tgalati4 on 2014-09-27
Also, grab a USB external keyboard and plug that in.  See if it works better than the laptop's keyboard.  Old laptops tend to get dirty inside which can cause strange issues.  I cleaned out my 2006 vintage Thinkpad T43p and I was amazed at how much dirt had accumulated.

---

### Post by Engineeringtech on 2014-09-27
> **tgalati4 said:**
> Look through your log files for errors.

```
more /var/log/syslog
```

Check your harddisk's SMART status.

```
sudo smartctl -a /dev/sda
```

I ran Syslog and the results are below.  Smartctl was not found.


Sep 27 11:16:22 600YGR rsyslogd: [origin software="rsyslogd" swVersion="5.8.11" x-pid="371" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Sep 27 11:16:46 600YGR anacron[915]: Job `cron.daily' terminated
Sep 27 11:16:46 600YGR anacron[915]: Normal exit (1 job run)
Sep 27 11:17:01 600YGR CRON[1954]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 27 11:22:16 600YGR wpa_supplicant[795]: wlan0: WPA: Group rekeying completed with 00:14:6c:25:2b:ae [GTK=TKIP]
Sep 27 11:52:16 600YGR wpa_supplicant[795]: wlan0: WPA: Group rekeying completed with 00:14:6c:25:2b:ae [GTK=TKIP]
Sep 27 12:17:01 600YGR CRON[2263]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 27 12:22:16 600YGR wpa_supplicant[795]: wlan0: WPA: Group rekeying completed with 00:14:6c:25:2b:ae [GTK=TKIP]
Sep 27 12:52:16 600YGR wpa_supplicant[795]: wlan0: WPA: Group rekeying completed with 00:14:6c:25:2b:ae [GTK=TKIP]
Sep 27 13:17:01 600YGR CRON[2689]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 27 13:22:16 600YGR wpa_supplicant[795]: wlan0: WPA: Group rekeying completed with 00:14:6c:25:2b:ae [GTK=TKIP]
Sep 27 13:52:16 600YGR wpa_supplicant[795]: wlan0: WPA: Group rekeying completed with 00:14:6c:25:2b:ae [GTK=TKIP]

---

### Post by Engineeringtech on 2014-09-27
Calm down?  Re-read his posts.  VASA1 insinuated that I was lying about my machine and the symptoms.   

Incidentally I struck the accusatory comment from my post, very quickly after I submitted it.  I won't be bullied.  But I'm no hot head either.

---

### Post by Engineeringtech on 2014-09-27
> **tgalati4 said:**
> Also, grab a USB external keyboard and plug that in.  See if it works better than the laptop's keyboard.  Old laptops tend to get dirty inside which can cause strange issues.  I cleaned out my 2006 vintage Thinkpad T43p and I was amazed at how much dirt had accumulated.

I'm afraid I don't have a USB keyboard to try.  And it still doesn't answer the question.. Why can I type with out problems in this forum (Firefox browser), the Sylpheed compose window, terminal windows, and all my Windows applications, but have  a severe typing delay with AbiWord?  I am not an experienced Linux user, but that does not sound like a hardware problem to me.


Ok now I am afraid I have to leave for  a while.  Health problems as usual.

---

### Post by tgalati4 on 2014-09-27
Open a terminal and run *abiword* in it.  Perhaps it has a --debug switch.  There are debugging symbols that you can load:

> tgalati4@Mint14-Extensa ~ $ apt-cache search abiword
libenchant-voikko - Voikko spell-checker libenchant plugin
abiword - efficient, featureful word processor with collaboration
abiword-common - efficient, featureful word processor with collaboration -- common files
**abiword-dbg - debugging symbols for abiword word processor**
abiword-plugin-grammar - grammar checking plugin for AbiWord
abiword-plugin-mathview - equation editor plugin for AbiWord


It's possible that you have a bad library file or a bad xinput binary that affects abiword's input but other programs use a different input pathway.

---

### Post by Engineeringtech on 2014-09-28
> **tgalati4 said:**
> Open a terminal and run *abiword* in it.  Perhaps it has a --debug switch.  There are debugging symbols that you can load:

It's possible that you have a bad library file or a bad xinput binary that affects abiword's input but other programs use a different input pathway.



Thanks again.  

 I ran the command "abiword -debug" in the terminal window..  Is that what you wanted?  I got the message, "unknown option -debug".   Then Abiword appeared.  I typed into the new document and did not see ANY typing delays!   Furthermore, the cursor was not flaky, and or covering part of what I type.    I wondered if the problem still appears when I open Abiword from the application launch bar.  And it did not!  Damn.  What happened?  I decided to close Abiword, and re-open it by double clicking one of the  documents I wrote over the past week.  And there is the typing delay and flaky cursor again!    So I started another new document and no typing delays.  So whatever the problem was, it seems to be gone now, unless I open one of the old documents I saved while the problem was evident.   

I think I have taken far too much of people's time here.   I apparently even alienated VASA1 by my comments.  All I really need is a word processing program or text editor that works.  Rather than keep trying to fix Abiword, I would love to find another app that will edit text files and RTF's.    But I can't find anything in Synaptic Package Manager, and I don't know how to do an installation without Synaptic.  If you can help me with this, I will be very grateful.  If not, I thank you anyway for all the help you have given me.    


a

---

### Post by Rex Bouwense on 2014-09-28
Try LibreOffice-Writer.  It is in the repositories.  It is heavier than Abiword but then you can do more with it.  You do not need to install all of the components of LibreOffice, just the Writer and dependencies.

---

### Post by Engineeringtech on 2014-09-29
Thanks for your help Rex.    I couldn't find LibreOffice in in the Synaptic Package Manager's software listing.  Then I realized you said "repositories".  I hunted through the Synaptic menus and found "repositories".  "Canonical Free and Open Source Software" was not checked.  Once I checked it, I was able to download and install LibreOffice.   I wonder if the people who create Ubuntu and Lubuntu realize that beginners like me don't know about these things.   

Anyway, Libre Office seems to work ok.  I'm not sure I need to find out what happened to AbiWord.  I guess I will mark this "solved".

---

### Post by tgalati4 on 2014-09-30
To see what switches are available in *abiword*, try 

```
abiword -?
```

or

```
abiword -h
```

When you opened one of your older documents that exhibited the problem, did you see any errors in the terminal?  It's possible that you had a strange font selected?

---

### Post by Engineeringtech on 2014-10-02
> **tgalati4 said:**
> To see what switches are available in *abiword*, try 

```
abiword -?
```

or

```
abiword -h
```

When you opened one of your older documents that exhibited the problem, did you see any errors in the terminal?  It's possible that you had a strange font selected?


I'm afraid I have already uninstalled AbiWord, so I don't know what switches were available.   As for fonts, I was using the default font, "Times New Roman".  I did try different fonts, but they did not help.  And I have opened documents that exhibited the problem with LibreOffice, and I can edit them without problem.

So there was something about AbiWord that just didn't work on my system.   I don't like the fact that I didn't find out what happened, but I'm the wrong person to diagnose a problem such as this.  I have LibreOffice, and will use that.

Thank you for all your help.

---

