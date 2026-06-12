---
title: "Ubuntu 12.04 Boot up stuck on black screen."
date: 2014-03-16
forum: General Help
---

### Post by Jack_Massey on 2014-03-16
Hey,

I have been using my ubuntu instillation for over a week now with no problems I had my drivers installed correctly and all of my programs running fine. Even dedicated graphics was working. My Laptop is the MSI GE60.

Now just recently I added some startup instructions namely "synclient SingleTapTimeout=0", "udisks --mount /dev/sda2"and "touchegg".

Now on reboot I was left at black screen with a non blinking cursor (No splash screen at all). I thought that it was just one of my startup programs so I went into root in recovery mode and removed the .desktop files. Then restarted. No difference.

 Some interesting things I have noted:
I have no /run/dbus directory which makes udisks fail.
Also here is my /var/log/boot.log

[CODE]
fsck from util-linux 2.20.1
/dev/sdb2: Superblock last mount time is in the future.
    (by less than a day, probably due to the hardware clock being incorrectly set)  FIXED.
/dev/sdb2: Superblock last write time is in the future.
    (by less than a day, probably due to the hardware clock being incorrectly set).  FIXED.
/dev/sdb2: clean, 350508/6766592 files, 4183350/27064064 blocks
 * Starting mDNS/DNS-SD daemon[74G[ OK ]
 * Starting Uncomplicated firewall[74G[ OK ]
 * Starting bluetooth daemon[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting configure network device[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting Mount network filesystems[74G[ OK ]
 * Starting Failsafe Boot Delay[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Stopping Mount network filesystems[74G[ OK ]
 * Starting configure network device[74G[ OK ]
 * Starting configure network device[74G[ OK ]
 * Stopping Failsafe Boot Delay[74G[ OK ]
 * Starting System V initialisation compatibility[74G[ OK ]
 * Starting modem connection manager[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting Bridge socket events into upstart[74G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting network connection manager[74G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting CUPS printing spooler/server[74G[ OK ]
 * Starting AppArmor profiles       [80G 
[74G[ OK ]
 * Setting sensors limits       [80G 
[74G[ OK ]
 * Stopping System V initialisation compatibility[74G[ OK ]
 * Starting System V runlevel compatibility[74G[ OK ]
 * Starting save kernel messages[74G[ OK ]
 * Starting automatic crash report generation[74G[ OK ]
 * Starting anac(h)ronistic cron[74G[ OK ]
 * Starting ACPI daemon[74G[ OK ]
 * Starting regular background program processing daemon[74G[ OK ]
 * Starting deferred execution scheduler[74G[ OK ]
 * Starting CPU interrupts balancing daemon[74G[ OK ]
Starting GNUstep distributed object mapper:  * Stopping anac(h)ronistic cron[74G[ OK ]
gdomap.
 * Starting crash report submission daemon[74G[ OK ]
 * Starting Userspace bootsplash[74G[ OK ]
 * Starting Send an event to indicate plymouth is up[74G[ OK ]
 * Starting LightDM Display Manager[74G[ OK ]
 * Stopping Send an event to indicate plymouth is up[74G[ OK ]
 * Not starting internet superserver: no services enabled
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * Stopping save kernel messages[74G[ OK ]
 * Stopping cold plug devices[74G[ OK ]
 * Stopping log initial device creation[74G[ OK ]
 * Starting configure network device security[74G[ OK ]
 * Starting save udev log and update rules[74G[ OK ]
 * Starting configure virtual network devices[74G[ OK ]
 * Stopping save udev log and update rules[74G[ OK ]
 * Stopping configure virtual network devices[74G[ OK ]
 * Stopping Userspace bootsplash[74G[ OK ]
[CODE]

Any help would be very appreciated.

---

