---
title: "X.org eating processor time, hard crashing"
date: 2007-08-02
forum: General Help
---

### Post by soulglo83 on 2007-08-02
I have found what I believe to be a problem with the X.org version in Feisty-current (1:7.2-0ubuntu11).  The symptoms include sudden 'freezing' of the system.  It appears to be hard locked, I will lose the ability to change caps lock or num lock, or to register anything from the keyboard.  Often the mouse will remain active, I can move it around the screen, but the interface beneath it is unresponsive.  Sound continues playing, but the screen (aside from the mouse) is never updated, it becomes static when the freeze occured.  I ssh'd to my sick little ubuntu box.  For those that are unfamiliar I'll introduce him:

ECS NF650iSLIT-A Motherboard
Intel E4400 Core 2 Duo
2GB of OCX topshelf 800mhz DDR2
4 IDE devices (3 hard drives, one optical [dvd burner])
Microsoft Comfort Curve 2000 Keyboard (their software sux, but their hardware rox!)
ATI X1600 PCI-E Video Card with fglrx v.8.34.8

uname -r:    2.6.20-16-generic

lspci
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation Unknown device 03bc (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: ATI Technologies Inc RV530 [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc RV530 [Radeon X1600] (Secondary)

Aside from the crash it runs very smoothly.  So when it occurs I ssh to it, and discover the following:

dmesg (the relevant output):
> [   43.185043] Bluetooth: RFCOMM ver 1.8
[   49.990477] eth0: no IPv6 routers present  
[  847.920293] nfsd: last server has exited     [COLOR="Red"] <CRASH OCCURS HERE![/COLOR]
[  847.920296] nfsd: unexporting all filesystems
[  847.920425] RPC: failed to contact portmap (errno -5).
[  848.960223] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  848.960283] NFSD: starting 90-second grace period
[ 7510.836986] [fglrx] PCIe has already been initialized. Reinitializing ...
[ 7510.845552] [fglrx] total      GART = 130023424
[ 7510.845557] [fglrx] free       GART = 114032640
[ 7510.845559] [fglrx] max single GART = 114032640
[ 7510.845560] [fglrx] total      LFB  = 268304384
[ 7510.845561] [fglrx] free       LFB  = 250474496
[ 7510.845562] [fglrx] max single LFB  = 250474496
[ 7510.845563] [fglrx] total      Inv  = 0
[ 7510.845565] [fglrx] free       Inv  = 0
[ 7510.845566] [fglrx] max single Inv  = 0
[ 7510.845567] [fglrx] total      TIM  = 0
[ 7812.894609] nfsd: last server has exited
[ 7812.894612] nfsd: unexporting all filesystems
[ 7812.894791] RPC: failed to contact portmap (errno -5).


So I removed nfs-common and nfs-kernel-server and the freezing persisted.  So then I ssh to the ubuntu box again and run:

ps -x: nothing fishy, all cpu time <0:20 etc.  

sudo ps -x: 
>  sudo ps -x
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
  PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:01 /sbin/init
    2 ?        S      0:00 [migration/0]
    3 ?        SN     0:00 [ksoftirqd/0]
    4 ?        S      0:00 [watchdog/0]
    5 ?        S      0:00 [migration/1]
    6 ?        SN     0:00 [ksoftirqd/1]
    7 ?        S      0:00 [watchdog/1]
    8 ?        S<     0:00 [events/0]
    9 ?        S<     0:00 [events/1]
   10 ?        S<     0:00 [khelper]
   11 ?        S<     0:00 [kthread]
   35 ?        S<     0:00 [kblockd/0]
   36 ?        R<     0:00 [kblockd/1]
   50 ?        S<     0:00 [kseriod]
  115 ?        S      0:00 [pdflush]
  116 ?        S      0:00 [pdflush]
  117 ?        S<     0:00 [kswapd0]
  118 ?        S<     0:00 [aio/0]
  119 ?        S<     0:00 [aio/1]
  747 ?        S      0:00 [kirqd]
 1972 ?        S<     0:00 [ksuspend_usbd]
 1973 ?        S<     0:00 [khubd]
 2173 ?        S<     0:00 [ata/0]
 2174 ?        S<     0:00 [ata/1]
 2175 ?        S<     0:00 [ata_aux]
 2185 ?        S<     0:00 [scsi_eh_0]
 2187 ?        S<     0:00 [scsi_eh_1]
 2236 ?        S<     0:00 [scsi_eh_2]
 2237 ?        S<     0:00 [scsi_eh_3]
 2468 ?        S<     0:01 [kjournald]
 2672 ?        S<s    0:00 /sbin/udevd --daemon
 3657 ?        S<     0:00 [kpsmoused]
 3845 ?        S<     0:00 [hda_codec]
 4213 ?        S<     0:00 [kjournald]
 4241 ?        Ss     0:00 /sbin/mount.ntfs-3g /dev/hda1 /media/hda1 -o rw,local
 4599 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 4600 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 4602 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 4604 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 4606 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 4607 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 4748 ?        Ds     0:00 /sbin/syslogd
 4803 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 4843 ?        S      0:00 hald-runner
 4882 ?        Ss     0:00 /usr/sbin/dhcdbd --system
 4897 ?        Ssl    0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkM
 4932 ?        Ss     0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/ru
 4945 ?        Ss     0:00 /usr/bin/system-tools-backends
 4946 ?        S      0:00 dbus-daemon --session --print-address --nofork
 4994 ?        Ss     0:00 /usr/sbin/gdm
 5120 ?        Ss     0:00 /usr/sbin/hpiod
 5300 ?        Ss     0:00 /usr/sbin/nmbd -D
 5302 ?        Ss     0:00 /usr/sbin/smbd -D
 5310 ?        S      0:00 /usr/sbin/smbd -D
 5322 ?        Ss     0:00 /usr/sbin/sshd
 5400 ?        Ss     0:00 /usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayal
 5428 ?        Ss     0:00 /usr/sbin/hcid -x -s
 5448 ?        S<     0:00 [krfcommd]
 5499 ?        Ss     0:00 /usr/sbin/cron
14202 ?        Ss     0:00 sshd: geraldo [priv]
14295 ?        S      0:00 /usr/sbin/gdm
14296 tty9     SLs+   5:20 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/: [COLOR="Red"] <--Jackpot![/COLOR]
17553 pts/1    R+     0:00 ps -x


so then I rebooted, and checked the same process was running albeit with a very low TIME.  I also noticed how its status is always SLs+ and it is the only process running with that status!  The processor time seems to climb as flash animations are viewed, videos are viewed, video transcoding, etc. is performed.  It does however continue to elevate, even during simple tasks like text editing or web browsing.  A possible related issue is that sometimes (randomly, its difficult to reproduce and happens infrequently, and might not even be related) my keyboard 'locks' like a button is depressed.  It is never the same button, and even after unplugging the keyboard it will continue to 'press' the locked button when a text input field comes into focus.

The crashing is unbearable.  I have for a long time been a huge Ubuntu fan (since warty!) it was my first linux distro, and I have (though I've experimented) always come home to Ubuntu.  I have read numerous forum posts, and googled to no end, but it seems like this problem with Xorg might be a problem of any nature, but it seems like one with a simple solution.  If i can find out what that status means (SLs+) and somehow change the niceness or something that Xorg is run with, I might be able to continue using Ubuntu.  This post is a summary of what I experience using multiple suggestions from [http://ubuntuforums.org/showthread.php?t=412125&highlight=feisty+freezes]("http://ubuntuforums.org/showthread.php?t=412125&highlight=feisty+freezes")
.  If I can provide anything at all that would be useful, let me know.

EDIT:  Further searching yields evidence their is already a confirmed bug report given importance low!  its [here]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/98783") I think there is a problem with the consensus regarding the bug.  If it was just collecting dumped pixmem wouldn't it's memory footprint shrink back to normal when firefox closes?  At the least, if it was dumped pixmem, the results of my xrestop wouldnt show X consuming 418megs less ram than 'top' shows, and xrestop only shows 7591K of pixmem used!  I have 2 gigs of ram, and after closing firefox after my TIME for the Xorg process is over 03:00, Firefox's is only 1:10 (With lots of tabs open).  After closing firefox it has no impact on Xorg process, and it only frees 90-110 megs of ram!  If i ssh to it and kill the Xorg process, my memory used is reduced from 100% (all of the available memory and 200megs of swap) to 226megs (total).  This is in my opinion clearly a problem with Xorg, and one that needs addressed!

---

### Post by soulglo83 on 2007-08-02
It sounds as though my problem, and many others regarding random 'freezing' might be related to: [http://forums.gentoo.org/viewtopic-t-537634-postdays-0-postorder-asc-highlight-xorg+memory+leak-start-100.html](http://forums.gentoo.org/viewtopic-t-537634-postdays-0-postorder-asc-highlight-xorg+memory+leak-start-100.html)

---

