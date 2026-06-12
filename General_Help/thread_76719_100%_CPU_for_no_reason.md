---
title: "100% CPU for no reason"
date: 2005-10-15
forum: General Help
---

### Post by cowlip on 2005-10-15
Hi, my pentium 3 866 mhz cpu seems ot constantly be at 50-100% load.  What is going on here?

---

### Post by gmatt on 2005-10-15
If you are using gnome and you have enabled the new transparencies and you do not have a graphics card (ecxept for an onboard one) you will put load on your cpu (since it is an older model) that just might explain why your load is 50%-100%. Try to trun off any uneeded features in gnome like the transparencies.

---

### Post by Lord Illidan on 2005-10-15
Try running top in a terminal and copy the output here...

---

### Post by cowlip on 2005-10-15
OK, thanks all.  I'm running an ATI All in Wonder 7200 and no transparencies are enabled, yet Xorg is taking up CPU like I've never seen before:

top - 17:40:17 up  4:39,  2 users,  load average: 2.04, 1.96, 1.54
Tasks:  89 total,   3 running,  86 sleeping,   0 stopped,   0 zombie
Cpu(s): 89.9% us,  4.5% sy,  0.0% ni,  4.9% id,  0.3% wa,  0.3% hi,  0.0% si
Mem:    386808k total,   376208k used,    10600k free,     6516k buffers
Swap:   345388k total,    78684k used,   266704k free,   120136k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6549 root      16   0 98036  44m 9468 R 58.0 11.9  35:02.63 Xorg
17705 owner     16   0 29596  14m 9792 R 25.0  3.7   4:21.28 gnome-system-mo
18426 owner     15   0 38304  13m 9252 S 10.2  3.7   0:02.35 gnome-terminal
 7097 owner     15   0  152m  28m  13m S  0.7  7.6   1:43.81 nautilus
18457 owner     16   0  2128 1088  844 R  0.7  0.3   0:00.12 top
 6590 cupsys    16   0  6284 1484 1024 S  0.3  0.4   0:13.34 cupsd
 7090 owner     16   0 16736 9196 6832 S  0.3  2.4   1:13.34 metacity
 7142 owner     15   0 28040  12m  10m S  0.3  3.2   0:10.04 kuake
17751 owner     15   0  158m 116m  14m S  0.3 30.7   1:21.69 opera
18420 owner     16   0  2128 1088  844 S  0.3  0.3   0:00.23 top
    1 root      16   0  1564  468  444 S  0.0  0.1   0:01.55 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.14 events/0
    4 root      11  -5     0    0    0 S  0.0  0.0   0:00.02 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   76 root      10  -5     0    0    0 S  0.0  0.0   0:00.59 kblockd/0
  102 root      15   0     0    0    0 S  0.0  0.0   0:00.90 pdflush
  105 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  104 root      15   0     0    0    0 S  0.0  0.0   0:03.53 kswapd0
  690 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kseriod
  853 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khubd
 2420 root      15   0     0    0    0 S  0.0  0.0   0:01.49 kjournald
 2560 root      12  -4  1660  496  444 S  0.0  0.1   0:00.31 udevd
 4317 root      15   0     0    0    0 S  0.0  0.0   0:00.32 kjournald
 4318 root      19   0     0    0    0 S  0.0  0.0   0:00.00 kjournald
 4319 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kjournald
 5185 root      23   0     0    0    0 S  0.0  0.0   0:00.01 kgameportd
 5694 dhcp      16   0  2328  524  520 S  0.0  0.1   0:00.00 dhclient3
 6019 root      16   0  1824  584  520 S  0.0  0.2   0:00.01 acpid
 6034 syslog    16   0  1764  668  592 S  0.0  0.2   0:00.07 syslogd

I attached this gnome systom monitor screenshot.  Is it normal for xorg to say tcp?

---

### Post by Joey French on 2005-10-15
Man, I just started a desklet for my cpu to tackle my crashing problem, and my processor, (AMD64 2800+) hit 100% when I opened firefox! What is going on here?

---

### Post by Tasu on 2005-10-15
Me too... well Firefox seems particularly hungry when 2 tabs are opened.. as soon as I open the second tab, system monitor shows a costant 100% cpu resources taken! O_O Wow... that made a great feature (tabbed browsing) a pain in the @$$ O_O. (sorry just kidding and trolling around with the last bard word... but indeed the problem is still really important, web browsing is one of the common things to do with a computer, this makes the computer quite useless while browsing...)

bye

il Tasu

---

### Post by vyruss on 2005-10-15
I've also said this in the development thread:

Try killing the update-notifier. As soon as I boot, it takes up huge CPU (and X.org along with it). As soon as it is killed, CPU goes back to normal.

I can only presume that something is wrong with the latest update to update-notifier ...

---

### Post by Joey French on 2005-10-27
What is update-notifier, and how does one go about killing it? You mean the little red guy that tells you about new updates? Mine is not running apparently, I haven't seen it since I moved to Breezy.

---

### Post by fizgig on 2005-11-01
[LEFT]Thanks vyruss.  Killing update-notifier did indeed bring my cpu back to normal.  Wish I didn't have to do that every time I boot up.
[/LEFT]

---

### Post by vyruss on 2005-11-01
[QUOTE=Joey French]What is update-notifier, and how does one go about killing it? You mean the little red guy that tells you about new updates? Mine is not running apparently, I haven't seen it since I moved to Breezy.[/QUOTE]

Open a terminal and type:```
killall update-notifier
```

---

### Post by felix_stegerman on 2005-11-01
[QUOTE=fizgig][LEFT]Thanks vyruss.  Killing update-notifier did indeed bring my cpu back to normal.  Wish I didn't have to do that every time I boot up.
[/LEFT][/QUOTE]

You can always uninstall it for now.


Felix

---

### Post by fizgig on 2005-11-01
If I try that it says it will uninstall the ubuntu-desktop package.  Doesn't sound good.

---

### Post by felix_stegerman on 2005-11-01
[QUOTE=fizgig]If I try that it says it will uninstall the ubuntu-desktop package.  Doesn't sound good.[/QUOTE]

Uninstalling the ubuntu-desktop package itself is not a problem.
It's just an empty package with a lot of dependencies on the packages
standard for a Ubuntu desktop install. It doesn't contain any files in itself
(okay it contains a changelog and a readme I think ;-)) ...

The only problem might be when you upgrade to a newer version of Ubuntu,
but you can always reinstall ubuntu-desktop before an upgrade and remove
the unwanted packages later ... ;-)


Felix

---

### Post by gboder on 2005-11-09
Hi,

I've had the same problem on my Inspiron 8200 (Intel P4-M 1.6Ghz / 512Mb / 60Go / nv440Go). The CPU was used at 100% all the time, I try to disable all graphical features like transparencies and console background, desktop background etc.. But this doesn't affect the CPU usage. After a start a top command into a shell (CTRL+ALT+F1, logged as root, perhaps sudo will works) and I see that the cupsd deamon was using 98% of the CPU !!! So I stoped it and disable it from automatic starting at startup !

Hope it was helpfull and understandible ;)


_SUMMARY_
1) Open a console as super user(ex root@tty1)
2) List all current process with top command
3) Identify the process where is using the most of CPU ressources
4) Search how to solve this issue
    a. Kill it and disable it
    b. Search on our friends google to solve this issue

---

