---
title: "fsck fscking?"
date: 2014-02-10
forum: General Help
---

### Post by PaulBx on 2014-02-10
I had a power failure last night and when I rebooted this morning I got some messages, so I wanted to fsck. I did "sudo touch /forcefsck" and rebooted. During the boot I got the impression an fsck might be going on but it flashed by so fast I couldn't be sure and I certainly couldn't read what it found.

I looked in /var/log/fsck at those two files but then found by searching here that that is not used any more (hmmm, why keep them around then - should I delete them?). I looked in /var/log/boot.log and found no evidence of an fsck. Here it is:

```
paul@len780:/var/log$ cat boot.log
Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ...   Reading all physical volumes.  This may take a while...
  Found volume group "lubuntu-vg" using metadata type lvm2
  2 logical volume(s) in volume group "lubuntu-vg" now active
/scripts/local-top/cryptroot: line 1: can't open /dev/mapper/lubuntu--vg-root: no such file
done.
Begin: Running /scripts/local-premount ... done.
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
modem-manager[1006]: <info>  ModemManager (version 0.6.0.0) starting...

modem-manager[1006]: <info>  Loaded plugin 'AnyData'

modem-manager[1006]: <info>  Loaded plugin 'Wavecom'

modem-manager[1006]: <info>  Loaded plugin 'Option'

modem-manager[1006]: <info>  Loaded plugin 'Gobi'

modem-manager[1006]: <info>  Loaded plugin 'Option High-Speed'

modem-manager[1006]: <info>  Loaded plugin 'Nokia'

modem-manager[1006]: <info>  Loaded plugin 'Ericsson MBM'

modem-manager[1006]: <info>  Loaded plugin 'Huawei'

modem-manager[1006]: <info>  Loaded plugin 'ZTE'

modem-manager[1006]: <info>  Loaded plugin 'X22X'

modem-manager[1006]: <info>  Loaded plugin 'MotoC'

modem-manager[1006]: <info>  Loaded plugin 'Novatel'

modem-manager[1006]: <info>  Loaded plugin 'Longcheer'

modem-manager[1006]: <info>  Loaded plugin 'Linktop'

modem-manager[1006]: <info>  Loaded plugin 'SimTech'

modem-manager[1006]: <info>  Loaded plugin 'Samsung'

modem-manager[1006]: <info>  Loaded plugin 'Sierra'

modem-manager[1006]: <info>  Loaded plugin 'Cinterion'

modem-manager[1006]: <info>  Loaded plugin 'Iridium'

modem-manager[1006]: <info>  Loaded plugin 'Generic'

modem-manager[1006]: <info>  Successfully loaded 20 plugins

 * Starting system logging daemon                                                                                                                                                                [ OK ]
 * Starting network connection manager                                                                                                                                                           [ OK ]
 * Starting mDNS/DNS-SD daemon                                                                                                                                                                   [ OK ]
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated                                                                                                     [ OK ]
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated                                                                                                     [fail]
 * Starting Bridge file events into upstart                                                                                                                                                      [ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles                                                                                                                                                                    [ OK ] 
 * Setting up X socket directories...                                                                                                                                                            [ OK ] 
 * Starting NTP server ntpd                                                                                                                                                                      [ OK ] 
 * Restoring resolver state...                                                                                                                                                                   [ OK ] 
 * Stopping System V initialisation compatibility                                                                                                                                                [ OK ]
 * Starting System V runlevel compatibility                                                                                                                                                      [ OK ]
 * Starting                                                                                                                                                                                      [ OK ]
 * Starting automatic crash report generation                                                                                                                                                    [ OK ]
 * Starting                                                                                                                                                                                      [ OK ]
 * Starting Restore Sound Card State                                                                                                                                                             [ OK ]
 * Starting                                                                                                                                                                                      [ OK ]
 * Starting                                                                                                                                                                                      [ OK ]
 * Starting save kernel messages                                                                                                                                                                 [ OK ]
 * Starting                                                                                                                                                                                      [ OK ]
 * Starting                                                                                                                                                                                      [ OK ]
 * Starting anac(h)ronistic cron                                                                                                                                                                 [ OK ]
 * Starting regular background program processing daemon                                                                                                                                         [ OK ]
 * Stopping Restore Sound Card State                                                                                                                                                             [ OK ]
 * Starting Initializes zram swaping                                                                                                                                                             [ OK ]
 * Starting crash report submission daemon                                                                                                                                                       [ OK ]
 * Starting CPU interrupts balancing daemon                                                                                                                                                      [ OK ]
 * Stopping save kernel messages                                                                                                                                                                 [ OK ]
 * Stopping anac(h)ronistic cron                                                                                                                                                                 [ OK ]
paul@len780:/var/log$ 

```

Grep tells me no fsck is in there. It's strange there is all that modem stuff since I don't have a modem. I suppose cups fails because I have no printer and haven't set one up.

Anyway I am scratching my head on this one. Did I get an fsck or not?

---

### Post by PaulBx on 2014-02-10
tune2fs on this device gives me "Last checked:             Mon Feb 10 09:01:53 2014" 
so I guess the fsck is actually happening but it's irritating that it does not show up in the log and that I can't see the details.

---

### Post by deadflowr on 2014-02-10
If it still concerns you I would recommend running a livecd session and then run fsck.
Use the e2fsck cheatsheet from [here]("https://help.ubuntu.com/community/FilesystemTroubleshooting#e2fsprogs_-_ext2.2C_ext3.2C_ext4_filesystems") to figure out the best usage.
The first one is normally the best option
```
fsck.ext4 -p /dev/sda1
```
but of course it also depend if your using the ext4 filesystem type.

But above all, don't run fsck on a mounted partition.

---

### Post by CharlesA on 2014-02-10
+1 to livecd.

Another way could be to remount / as read only, but it can get iffy if there are problems with the file system, which is why you should run it off a livecd.

See [here]("http://wiki.gandi.net/en/iaas/references/server/fsck"), if you really want to do it that way, but I still recommend going the liveCD route.

---

### Post by PaulBx on 2014-02-10
I could go livecd, but that is pretty lame if you think about it. First, I am using encryption (my choice) as well as LVM (not my choice). I really need multiple runs, both of the native drive and of the encrypted file system. I suppose I could figure out all the steps; I have done it with Puppy Linux (without the complicating factor of LVM though). But this seems pretty basic to operating systems. Windows gets it right - this time. Wish I could just tell it to go chkdsk and let the boot time environment figure out the gory details.

---

### Post by CharlesA on 2014-02-10
Well, that's what you were doing when you did touch /forcefsck....

It should have notified you if there were errors.

---

### Post by Herman on 2014-02-11
It's really not that difficult to use the Live CD to run a file system check in an encrypted LVM nowadays.

Just boot your Live CD and open Disk Manager, unlock your disk by clicking on the button for it and type your encryption password.
Then look for the encrypted volume icon which will appear, select that and click on the file system check button. 
Simple! :)

---

### Post by IPvFletch on 2014-02-11
FWIW, I just found out last night every time I boot Ubuntu 12.4.4 LTS it is doing an fsck before it even loads the kernel. I can see it in my msgs (right before the screen starts scrolling like crazy). It does an fsck on /dev/sda (my main disk).

---

