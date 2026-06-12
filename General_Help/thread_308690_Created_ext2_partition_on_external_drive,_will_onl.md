---
title: "Created ext2 partition on external drive, will only mount read-only"
date: 2006-11-28
forum: General Help
---

### Post by JPorter on 2006-11-28
Hello all!

I am running the Edgy LiveCD (PPC) and attempting to reconfigure a 320GB external usb2.0 hard drive so that I can access it from Ubuntu, MacOSX and Windows.

The only fully cross-platform filesystem that will handle files larger than 4GB that I know of is ext2, using various open source drivers on the Windows and OSX platforms.


I have created a 280GB ext2 partition (tried with both gparted and fdisk), which completes successfully in either case.

The system automounts the drive once I turn automounting back on and reconnect the drive.


Here's my issue...

The ext2 partition appears on the desktop and is accessible, but read only.     I can't seem to get the drive to automount with read/write permissions.

Can anyone help a newb?


Thanks,
JPorter


P.S. - One interesting aside... can't access the partition under OSX either, most of the information in the permissions info is greyed out, with no owner info.

---

### Post by JPorter on 2006-11-28
By the way, 

I'm familiar with the fact that automount is governed by the settings in /usr/share/hal/fdi/policy/10osvendor but I'm not clear on what I need to edit there in order to have proper permissions assigned to external drives that I attach.

Any guidance would be greatly appreciated.

---

### Post by taurus on 2006-11-28
With ext2 filesystem, you can change the permissions with the chmod command!!!

```
sudo chmod 777 <mount point>
```

---

### Post by alexicon on 2007-09-07
i have a similar issue with an external drive automounting but as read only. well.. it seems to be able to write if i sudo. saw the file on there, then i click the file and it disappears. just general bad behaviour of this external drive. 

its a seagate freeagent go 160gb. i first had it ntfs, using the ntfs-3g drivers, which seemed to do the trick although the drived timed out rather quickly, i think that was an issue i could change from windows. anyway that worked for about a week transferring small files. then suddenly loads of stuff on the drive disappeared, some directories i hadnt even written to before. the one directory that remained that i had added, only had about 1/3 of the stuff i had copied over. 

thinking it was bad ntfs drivers i reformatted the drive to fat32 since my ipod works well still. this worked for about 10 minutes, started copying over all my dotfiles, then it suddenly changed to read only mode... got frustrated with the thing, so decided i'll just format it to ext3, hoping that native linux filesystem would sort the thing out. no joy. i was able to copy over one file using sudo, but i shouldnt have to do that. now the file when i click on it disappears, then comes back with some broken icon instead of the preview, i click that and that disappears... getting some weird errors on the thing, but i dont know why. reformats went smoothly and without error. 


tail /var/log/messages
Sep  7 04:48:53 phaedrus kernel: [22890.540000] sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Sep  7 04:48:53 phaedrus kernel: [22890.540000]     Additional sense: Logical unit not ready, initializing command required
Sep  7 04:48:53 phaedrus kernel: [22890.540000] end_request: I/O error, dev sdb, sector 12375
Sep  7 04:48:53 phaedrus kernel: [22890.544000] sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Sep  7 04:48:53 phaedrus kernel: [22890.544000]     Additional sense: Logical unit not ready, initializing command required
Sep  7 04:48:53 phaedrus kernel: [22890.544000] end_request: I/O error, dev sdb, sector 63
Sep  7 04:48:53 phaedrus kernel: [22890.544000] lost page write due to I/O error on sdb1
Sep  7 04:49:01 phaedrus kernel: [22897.724000] sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
Sep  7 04:49:01 phaedrus kernel: [22897.724000]     Additional sense: Logical unit not ready, initializing command required
Sep  7 04:49:01 phaedrus kernel: [22897.724000] end_request: I/O error, dev sdb, sector 12375


dmesg
[part]
[ 2146.484000] EXT3 FS on sda9, internal journal
[ 2146.484000] EXT3-fs: mounted filesystem with ordered data mode.
[ 7115.820000] ipw3945: Microcode SW error detected.  Restarting.
[ 7115.820000] ipw3945: request scan called when driver not ready.
[ 7116.820000] ipw3945: Can't stop Rx DMA.
[ 7117.100000] ipw3945: Detected geography ABG (13 802.11bg channels, 12 802.11a channels)
[ 7118.624000] ipw3945: association process canceled
[22131.992000] sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[22131.992000]     Additional sense: Logical unit not ready, initializing command required
[22131.992000] end_request: I/O error, dev sdb, sector 12479
[22131.996000] sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[22131.996000]     Additional sense: Logical unit not ready, initializing command required
[22131.996000] end_request: I/O error, dev sdb, sector 12495
[22131.996000] Buffer I/O error on device sdb1, logical block 1554
[22131.996000] lost page write due to I/O error on sdb1
[22131.996000] Aborting journal on device sdb1.
[22166.412000] sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[22166.412000]     Additional sense: Logical unit not ready, initializing command required
[22166.412000] end_request: I/O error, dev sdb, sector 8279
[22166.412000] Buffer I/O error on device sdb1, logical block 1027
[22166.412000] lost page write due to I/O error on sdb1
[22890.540000] sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[22890.540000]     Additional sense: Logical unit not ready, initializing command required
[22890.540000] end_request: I/O error, dev sdb, sector 12375
[22890.540000] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
[22890.544000] sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[22890.544000]     Additional sense: Logical unit not ready, initializing command required
[22890.544000] end_request: I/O error, dev sdb, sector 63
[22890.544000] Buffer I/O error on device sdb1, logical block 0
[22890.544000] lost page write due to I/O error on sdb1
[22897.724000] sd 5:0:0:0: Device not ready: <6>: Current: sense key: Not Ready
[22897.724000]     Additional sense: Logical unit not ready, initializing command required
[22897.724000] end_request: I/O error, dev sdb, sector 12375
[22897.748000] EXT3-fs error (device sdb1): ext3_find_entry: reading directory #2 offset 0
[22899.884000] ext3_abort called.
[22899.884000] EXT3-fs error (device sdb1): ext3_journal_start_sb: Detected aborted journal
[22899.884000] Remounting filesystem read-only


cat /etc/mtab
[part]
/dev/sdb1 /media/disk ext3 rw,noexec,nosuid,nodev 0 0


this is on feisty fawn fully updated 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux 

dont know whats happening here, but will try it on a fresh feisty install later. might also try another distro if i can spare the hdd space for it, although probably not as i got this drive to free up some space :P anyway, any suggestions welcome

ps just saw this link now too
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg426888.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg426888.html)
similar to my problem, but i've read a lot of weird stuff about external hdds recently :/

---

### Post by alexicon on 2007-09-09
got a solution for mine when i looked up freeagent external drives..

think you might have a udev problem, have a look on the forums for your specific drive maybe that will help.

---

