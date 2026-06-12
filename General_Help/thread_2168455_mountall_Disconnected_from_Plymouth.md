---
title: "mountall: Disconnected from Plymouth"
date: 2013-08-17
forum: General Help
---

### Post by Cory_Mittleider on 2013-08-17
I've recently upgraded through the package manager from 10.04 to 12.04.  During startup I get a message mountall: Disconnected from Plymouth and it just hangs out at that screen.  I've read through all kinds of other threads with this problem, but nothing I've tried has repaired it.  

Please help.
Cory

---

### Post by Cory_Mittleider on 2013-08-18
I've modified my grub to remove the quiet splash hoping it would solve this problem.  It still didn't help but now it stops on a different line of output that says something like Stopping System V Compatability.  I'm able to alt+F2, login, and startx to get a somewhat functional computer.  I've pasted my boot log below from this boot.  Hopefully someone can help identify the hangup here for me.


```
Begin: Loading essential drivers ... done.Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... done.
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
/dev/sda5: clean, 700677/2747136 files, 3263077/10985984 blocks
/dev/sda7: clean, 53703/3629056 files, 3990574/14502144 blocks
 * Starting mDNS/DNS-SD daemon[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
 * Starting Mount network filesystems[122G[ OK ]
 * Starting Failsafe Boot Delay[122G[ OK ]
 * Starting Upstart job to start portmap on boot only[122G[ OK ]
 * Stopping Upstart job to start portmap on boot only[122G[ OK ]
 * Stopping Mount network filesystems[122G[ OK ]
 * Starting RPC port mapper[122G[ OK ]
 * Starting configure network device[122G[ OK ]
 * Stopping Failsafe Boot Delay[122G[ OK ]
 * Starting System V initialisation compatibility[122G[ OK ]
 * Starting modem connection manager[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
 * Starting network connection manager[122G[ OK ]
 * Starting Bridge socket events into upstart[122G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles       [128G 
[122G[ OK ]
 * Setting sensors limits       [128G 
[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
 * Starting configure network device[122G[ OK ]
 * Stopping cold plug devices[122G[ OK ]
 * Stopping log initial device creation[122G[ OK ]
 * Stopping System V initialisation compatibility[122G[ OK ]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
saned disabled; edit /etc/default/saned
 * Starting enable remaining boot-time encrypted block devices[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
 * Starting configure virtual network devices[122G[ OK ]
 * Stopping enable remaining boot-time encrypted block devices[122G[ OK ]
 * Stopping configure virtual network devices[122G[ OK ]
 * Starting System V runlevel compatibility[122G[ OK ]
 * Starting automatic crash report generation[122G[ OK ]
 * Starting CPU interrupts balancing daemon[122G[ OK ]
 * Starting deferred execution scheduler[122G[ OK ]
 * Starting regular background program processing daemon[122G[ OK ]
 * Starting GNOME Display Manager[122G[ OK ]
 * Starting LightDM Display Manager[122G[ OK ]
 * Starting ACPI daemon[122G[ OK ]
 * Starting anac(h)ronistic cron[122G[ OK ]
 * Starting save kernel messages[122G[ OK ]
 * Starting crash report submission daemon[122G[ OK ]
 * Stopping Send an event to indicate plymouth is up[122G[ OK ]
 * Stopping anac(h)ronistic cron[122G[ OK ]
 * Stopping LightDM Display Manager[122G[ OK ]
 * Stopping save kernel messages[122G[ OK ]
```

---

### Post by Cory_Mittleider on 2013-08-22
After following the procedure [here]("http://ubuntuforums.org/showthread.php?t=1859820&page=5") on post 47 it will restart once on its own.  The second boot continues gets me back to the same problem.  The boot will even work without the xorg.conf file, i've found out that the new X doesn't need the xorg.conf.  Also, with the fglrx driver completely removed I still have a booting problem so I figured out it wasn't the graphics driver.

When I booted to the blank screen I was able to hit alt+F2 to access another virtual terminal and login.  When i tried to start gdm i got a message that said gdm was already running, but I was able to startx.  When I did this gnome did not load I was just given my windowed environment and shown the desktop.  After some more looking I realized that it's gdm that was actually the reason my startup seemed to fail.  After doing some reading [here]("https://bbs.archlinux.org/viewtopic.php?id=133179") and going to the gnome wiki linked on post 8 I ran dpkg-reconfigure lightdm and selected that as my desktop manager, and my computer now starts reliably. 

I am still occasionally having trouble shutting down, it seems to hang, but that's a lot better than not starting.

---

