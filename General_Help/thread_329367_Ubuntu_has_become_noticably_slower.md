---
title: "Ubuntu has become noticably slower"
date: 2007-01-01
forum: General Help
---

### Post by chris90uk on 2007-01-01
Hi everyone

Here is some background information. I have Ubuntu Dapper installed on a HP Pavillion laptop with 512mb ram and a Sempron processor. First thing I did when I got it is install Ubuntu, and set it all up nicely. The system was stable.

I wanted to try some different window managers. I had already tried XFCE before, and I quite liked it on my older desktop, but I thought I'd try KDE as well to see what it is like. Now, I have gone back to Gnome. Now I have noticed that my computer is more unstable and slower - sometimes when I log out, I will just get a white screen and have to turn it off with the button, and it takes longer to open the applications menu (a long time at startup). 

I don't know what has caused this slowdown - do you suspect that I have too much installed on my computer, or even that the actual computer is deteriorating?

I don't want to get back into the old routine with Windows where I used to reinstall it every few months after it became unbearably slow and crashy.

Thanks!

---

### Post by moshuptrail on 2007-01-01
I tried a few other window managers and it got my system pretty messy.  (although I don't remember it getting slow) I was seeing all kinds of stuff in the menus that was left over from other WM's.  So I just re-installed the version I wanted from scratch.  It only takes about 1/2 hour.  Not like windows!  

If that's not an option for you, try opening a Terminal and typing "top".  It will show you the top CPU users.  Cut and paste here and see if we can help.

---

### Post by adaptr on 2007-01-01
The amount of software installed really doesn't influence Linux systems much.
The only situation where you might notice a performance decrease is when you are actually *using* a significant number of KDE applications - that is, applications that need (and use) KDE libraries, or the Qt window toolkit.

Those eat memory, even more than Gnome components do - in essence it means you have 2 desktop systems loaded at the same time, even if you're not using the KDE look-and-feel (which is only a small part of the KDE desktop system).

And swapping on a laptop - argh.

That would be the first place to look - monitor your systems'  memory and swap usage; if it's using swap on a regular basis, then you have a memory issue.

So no, it's not Ubuntu - just remove whatever KDE apps you don't need anymore, and particularly look for any K* applications still in use - use System Monitor or something like that.

---

### Post by chris90uk on 2007-01-01
top - 19:57:06 up 20 min,  2 users,  load average: 0.19, 0.31, 0.28
Tasks:  77 total,   3 running,  74 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.6% us,  1.3% sy,  0.0% ni, 89.7% id,  0.0% wa,  1.3% hi,  0.0% si
Mem:    384944k total,   377400k used,     7544k free,    10016k buffers
Swap:  1124508k total,        0k used,  1124508k free,   195880k cached
 Unknown command - try 'h' for help
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5878 chris     15   0 33836  14m 9336 S  5.0  3.9   0:02.14 gnome-terminal
 4304 root      15   0 55224  32m 9984 S  2.0  8.6   0:45.57 Xorg
 5150 chris     15   0  200m  75m  20m R  0.7 20.1   1:56.13 firefox-bin
 5075 chris     15   0 73392  18m  13m S  0.3  4.9   0:03.26 gnome-panel
 5094 chris     15   0 55264 9016 7276 S  0.3  2.3   0:01.53 gnome-cups-icon
    1 root      16   0  1564  532  460 S  0.0  0.1   0:01.03 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.08 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 kblockd/0
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  125 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  126 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  128 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  127 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  135 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid-work-0
  718 root      10  -5     0    0    0 S  0.0  0.0   0:00.11 kseriod
 1830 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1914 root      15   0     0    0    0 S  0.0  0.0   0:00.04 kjournald
 2143 root      19  -4  2432  924  368 S  0.0  0.2   0:00.26 udevd
 2910 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 3483 dhcp      14  -2  2336  540  236 S  0.0  0.1   0:00.00 dhclient3
 3834 root      16   0  2156 1196  644 S  0.0  0.3   0:00.00 acpid
 3920 syslog    16   0  1764  684  564 S  0.0  0.2   0:00.00 syslogd
 3946 root      15   0  1684  500  412 S  0.0  0.1   0:00.01 dd
 3948 klog      18   0  2404 1332  388 S  0.0  0.3   0:00.06 klogd
 4270 root      15   0 10916 1808 1216 S  0.0  0.5   0:00.00 gdm
 4291 root      16   0 11352 2668 2016 S  0.0  0.7   0:00.02 gdm
 4311 hplip     16   0 12876  920  696 S  0.0  0.2   0:00.00 hpiod
 4316 hplip     15   0  9408 4672 1096 S  0.0  1.2   0:00.01 python
 4375 cupsys    16   0  4328 2036 1384 S  0.0  0.5   0:01.56 cupsd
 4445 clamav    16   0  5220 1284 1000 S  0.0  0.3   0:00.01 freshclam
 4461 messageb  16   0  2196  852  668 S  0.0  0.2   0:00.04 dbus-daemon
 4476 haldaemo  16   0  6808 5400 1556 S  0.0  1.4   0:01.05 hald
chris@chris-laptop:~$

Thanks for offering to help - hope this makes sense to you.

---

### Post by moshuptrail on 2007-01-01
Look at the display of top:

It lists processes.  Those that are user "chris" are the ones you have the most control over - they got started when you logged in.

What it's showing at the instant of the snapshot is that the highest CPU using process is your gnome-terminal at about 5.0%, followed by xorg and Firefox.  But the total CPU usage is really pretty low, 7.6%.  Memory use is 377k out of 384k.  Not bad.  And swap file use is 0% which is good.  You should only use swap file when you run out of memory for all the programs you are running.

So I can see no "resource" cause for a slow system.  Your system has adequate CPU and memory for what it's doing.

What are you doing when it's "slow"?  (post the last 10-15 lines from dmesg just in case)

---

### Post by chris90uk on 2007-01-01
There are times when I expect it to go slow, like when I use LimeWire or something, but sometimes it randomly decides to slow down and when I log off it freezes. Firefox also crashes a lot more often now.

---

### Post by moshuptrail on 2007-01-01
You might try disabling IPv6.  It's an extension of IP addressing that allows addresses longer than the current 192.168,1.1 type addresses.  This seems to help Firefox especially.

[http://www.ubuntuforums.org/showthread.php?t=87798&highlight=disable+IPv6](http://www.ubuntuforums.org/showthread.php?t=87798&highlight=disable+IPv6)

---

