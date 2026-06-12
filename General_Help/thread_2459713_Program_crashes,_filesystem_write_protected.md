---
title: "Program crashes, filesystem write protected"
date: 2021-03-24
forum: General Help
---

### Post by Cadryc on 2021-03-24
I have a problem with programs not starting some times and crashing after a while. I started deluge in terminal and got this output during the crash
Note: i transleated some words because they where in my language. If it is confusing I can change system language to English.

```
03:37:26 [ERROR   ][deluge.config                     :489 ] Error writing new config file: [Errno 30] filesystem write protected: '/tmp/stats.totals.ig_nh_64'
corrupted double-linked list
Aborted (SIGABRT) (memory print created)
```

When I type deluge again in the terminal and hit enter I get this output
```
OSError: [Errno 30] filesystem write protected: b'/home/john/.config/deluge/ipc/deluge-gtk.lock'
```

Then I tried to start nautilus to check permissions on those folders (yeah I'm really not a linux guru...) I get this output

```
sudo nautilus
(org.gnome.Nautilus:13019): GLib-GIO-CRITICAL **: 12:32:57.673: g_dbus_proxy_call_internal: assertion 'G_IS_DBUS_PROXY (proxy)' failed
Failed to create random directory /tmp/pulse-LhW3uvrsqRsR: File system write protected
Failed to symlink /root/.config/pulse/cfa69d4a78a746f4b21dee21d64bd29e-runtime.tmp: Filesystem write protected
Failed to create random directory /tmp/pulse-ft4GMp61QtuN: Filesystem write protected
Failed to symlink /root/.config/pulse/cfa69d4a78a746f4b21dee21d64bd29e-runtime.tmp: Filesystem write protected

```

memtest didn't show any problems after 5 passes.

---

### Post by dinkidonk on 2021-03-24
The system drive is mounted with the option "errors=remount-ro" which means that if errors occur on the volume, it is remounted as read-only. This may be the cause of your problem and I would suggest that you examine the SMART data for the drive and maybe scan it for errors with "badblocks" or repair damage to the file system with "fsck".

---

### Post by Impavidus on 2021-03-24
When there's an error accessing your file system, the relevant filesystem (partition) is remounted in read-only mode. This to prevent further damage until the filesystem has been repaired and/or backups have been created. This behaviour is controlled through the settings in your /etc/fstab.

---

### Post by Cadryc on 2021-03-24
> **dinkidonk said:**
> The system drive is mounted with the option "errors=remount-ro" which means that if errors occur on the volume, it is remounted as read-only. This may be the cause of your problem and I would suggest that you examine the SMART data for the drive and maybe scan it for errors with "badblocks" or repair damage to the file system with "fsck".

> **Impavidus said:**
> When there's an error accessing your file system, the relevant filesystem (partition) is remounted in read-only mode. This to prevent further damage until the filesystem has been repaired and/or backups have been created. This behaviour is controlled through the settings in your /etc/fstab.

Thanks for you answer. SMART, throught Disk utility in Ubuntu, says "Disk is ok, 16 bad sectors". Those 16 bad sectors have been there for a long time. It is an Intel SSD I have used in my main computer for years and I got 16 bad sectors there as well since some years ago but the SSD worked fine anyway.

However, now I'm using the SSD with a SATA to IDE adapter (well aware of the limitations), because I'm trying to use another old computer as a server. The first adapter didn't work at all, the second seemed to work during install but ubuntu hanged within the hour. The third and current adapter worked fine and Ubuntu haven't had a hickup that I noticed while I followed some guides to setup mdadm, nfs etc.

But probably this is where the problem lies then... I got a PATA drive but it is many years older than the SSD so I took my chances with the SSD.

Unless you have some suitable mount options or tweaks up your sleeves I'll try the other disk. Do you think I can connect my SSD through my SATA to USB adapter and copy my SSD installation to the PATA drive within a live session, and then install grub? It would be nice if I could bring my configurations with me...

---

### Post by dinkidonk on 2021-03-24
The problem with SSD's and adapters is, that TRIM usually not work with adapters (definitely not with the IDE/PATA interface). Some USB adapters support the UASP which implies TRIM, though.

TRIM is used to prepare free pages for new write operations and if that is not done regularly, the drive will have to do it "on the fly" and this may slow the drive so much that the system may consider it hanging / defunct. Not using TRIM on a regular basis will both impact performance and life time of a SSD, so you are slowly killing your SSD.

---

### Post by Cadryc on 2021-03-24
> **dinkidonk said:**
> The problem with SSD's and adapters is, that TRIM usually not work with adapters (definitely not with the IDE/PATA interface). Some USB adapters support the UASP which implies TRIM, though.

TRIM is used to prepare free pages for new write operations and if that is not done regularly, the drive will have to do it "on the fly" and this may slow the drive so much that the system may consider it hanging / defunct. Not using TRIM on a regular basis will both impact performance and life time of a SSD, so you are slowly killing your SSD.
Oh, I read that TRIM was ATA dependent, not SATA, and should work with PATA, but I assume now that it depends on the adapter. I also assume there is no way I can add a cronjob or something to manually run TRIM, because if that would work, TRIM would be working now... am I right? 

Does a non zero value indicate TRIM support? [https://bbs.archlinux.org/viewtopic.php?pid=1711776#p1711776](https://bbs.archlinux.org/viewtopic.php?pid=1711776#p1711776)
```
~$ lsblk -D
NAME      DISC-ALN DISC-GRAN DISC-MAX DISC-ZERO
sda              0      512B       2G         0
&#9500;&#9472;sda1           0      512B       2G         0
&#9492;&#9472;sda2           0      512B       2G         0
sdb              0        0B       0B         0
............

```

---

### Post by TheFu on 2021-03-24
On Ubuntu trim used to get run once a week, automatically for all recognized SSD storage.  I swear it was still doing this 6 months ago. I just looked in /etc/cron.weekly/ and didn't see anything related to **fstrim**. You can run it manually, if you like.  I'm a little curious about what happened to the automatic fstrim invocation. Perhaps it was added to systemd somewhere? 
Found it: 
```
/etc/systemd/system/timers.target.wants/fstrim.timer:Documentation=man:fstrim
/etc/systemd/system/timers.target.wants/fstrim.timer
/lib/systemd/system/fstrim.timer
```
It is run weekly on my system.

Whether your SSD is recognized as an SSD or not is a different question.

BTW, whenever posting storage output from any commands, we NEVER, EVER, EVER, need to see any loop crap. Please edit that out - since it just clutters the output.

The only times I've seen an SSD go read-only is just before it died.  Backup your data, keep those backups current, perhaps get a replacement.  When mine went read-only, it could be coaxed to read-write with a reboot. About a month after the first time, it was dead, Jim.
All storage fails.  Our goal it so use it as long as possible, but not have any data loss and minimize bad performance.

---

### Post by Cadryc on 2021-03-24
> **TheFu said:**
> On Ubuntu trim used to get run once a week, automatically for all recognized SSD storage.  I swear it was still doing this 6 months ago. I just looked in /etc/cron.weekly/ and didn't see anything related to **fstrim**. You can run it manually, if you like.  I'm a little curious about what happened to the automatic fstrim invocation. Perhaps it was added to systemd somewhere? 
Found it: 
```
/etc/systemd/system/timers.target.wants/fstrim.timer:Documentation=man:fstrim
/etc/systemd/system/timers.target.wants/fstrim.timer
/lib/systemd/system/fstrim.timer
```
It is run weekly on my system.

Whether your SSD is recognized as an SSD or not is a different question.

BTW, whenever posting storage output from any commands, we NEVER, EVER, EVER, need to see any loop crap. Please edit that out - since it just clutters the output.

The only times I've seen an SSD go read-only is just before it died.  Backup your data, keep those backups current, perhaps get a replacement.  When mine went read-only, it could be coaxed to read-write with a reboot. About a month after the first time, it was dead, Jim.
All storage fails.  Our goal it so use it as long as possible, but not have any data loss and minimize bad performance.

/etc/systemd/system/timers.target.wants/fstrim.timer  reads
```
[Unit]
Description=Discard unused blocks once a week
Documentation=man:fstrim
ConditionVirtualization=!container

[Timer]
OnCalendar=weekly
AccuracySec=1h
Persistent=true

[Install]
WantedBy=timers.target
```

and sudo /sbin/fstrim -av  gives 
```
fstrim: /: 59,7 GiB (64129257472 bytes) trimmed on /dev/sda2
```

Can one conclude from this that trim is performed on my SSD (sda) on a weekly basis?

I got a newer SSD for my primary computer and thought I might get a couple of years out of this old SSD in my server. Performance gains over PATA disk is noticable even with the IDE adapter. I got an IDE drive but it is even older than the SSD, I don't really want to buy new motherboard and all that comes with, I justified the purchase of 4 disks for myself with "I can utilize the old computer that is just standing there..." but perhaps that is what I will have to do.

---

### Post by TheFu on 2021-03-24
>  Whether your SSD is recognized as an SSD or not is a different question.
I said that because it would depend on the OS recognizing the SSD in your system through all the funky conversion/connectors as an SSD.  I wouldn't know if it does or not.

---

### Post by Cadryc on 2021-03-25
> **TheFu said:**
> I said that because it would depend on the OS recognizing the SSD in your system through all the funky conversion/connectors as an SSD.  I wouldn't know if it does or not.
I understand. Anyway I ran the trim command and same thing happened again so I guess the question whether automatic trim is working or not is moot. I'm gonna take my chances with my antique PATA drive.

Thanks for your help :-D

---

