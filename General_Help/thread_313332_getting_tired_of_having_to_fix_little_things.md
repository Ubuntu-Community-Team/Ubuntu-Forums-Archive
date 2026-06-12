---
title: "getting tired of having to fix little things"
date: 2006-12-05
forum: General Help
---

### Post by shane2peru on 2006-12-05
I was trying to backup my /home dir with this command:
```

tar zcvpf /home/shane/storage/homebackup`date +%Y-%m-%d`.tar.gz /home/shane/ --exclude=/home/shane/storage --exclude=/home/shane/Portable --exclude=/home/shane/Pictures --exclude=/home/shane/.java

```I have also tried this code:

and ```

tar zcvpf /home/shane/storage/home2backup`date +%Y-%m-%d`.tar.gz --exclude=/home/shane/storage --exclude=/home/shane/Portable --exclude=/home/shane/Pictures --exclude=/home/shane/.java /home/shane/

```I get this error either way.
```

tar: Error exit delayed from previous errors
shane@shane-laptop:~$ dmesg | tail
[17179635.060000] Bluetooth: RFCOMM TTY layer initialized
[17179635.060000] Bluetooth: RFCOMM ver 1.7
[17179675.168000] kjournald starting.  Commit interval 5 seconds
[17179675.172000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[17179675.184000] EXT3 FS on sda1, internal journal
[17179675.184000] EXT3-fs: mounted filesystem with ordered data mode.
[17180344.984000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
[17180345.492000] psmouse.c: resync failed, issuing reconnect request
[17180346.184000] input: PS/2 Mouse as /class/input/input4
[17180346.204000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input5

```Before it had errors about vmmon, and setting the clock rate .... blah blah blah, I uninstalled vmware, and now it still don't work. ](*,)  I'm really getting tired of these annoyances.  Can anyone tell me how to fix this?

Oh, also when I just tried to copy some lines out of the terminal window, I highlighted hit ctrl-C and the window just disappeared.


Also my /media/Portable and /media/storage don't auto mount on boot.  Here is my fstab: ```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=ad9fb93c-e1e4-4c63-8999-3e63e3fb2425 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=d098cad6-cbf5-49b5-93d2-a6fc860406ec /home           ext3    defaults        0       2
# /dev/hda1
UUID=C4D0324CD0324548 /media/XP       ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
#UUID=71b41fdc-4b6e-44c6-a6ee-669693cfa53d /media/dapperroot ext3    defaults        0       2
# /dev/hda6
UUID=005a661b-b311-4fac-abf1-b707011472c8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
[COLOR=Red]/dev/sda2     /media/Portable vfat user,auto,umask=000         0 0
/dev/sda1    /media/storage  ext3 user,auto         0 0[/COLOR]
/dev/sdb5     /media/XPStorage vfat user,auto,umask=000         0 0
/dev/sdb1     /media/Ubuntu ext3 user,auto         0 0

```I highlighted the two pertinent ones red for you. I'm really starting to have my doubts about this Linux stuff. I have installed about 20 different times, (ok about 12 of those were my fault, and me learning) but it is getting old. I'm currently using Edgy 6.10 - on a Toshiba Laptop. with some 700+MB Ram, with a 1400 mhz processor. Oh, and in case you need it, here is my fdisk -l ```

sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2493    20024991    7  HPFS/NTFS
/dev/hda2            2494        3825    10699290   83  Linux
/dev/hda3            3826        4463     5124735   83  Linux
/dev/hda4            4464        4864     3221032+   5  Extended
/dev/hda5            4464        4830     2947896   83  Linux
/dev/hda6            4831        4864      273073+  82  Linux swap / Solaris

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2295    18434556   83  Linux
/dev/sda2   *        2296        4863    20627460    b  W95 FAT32

```any help would be appreciated.

Shane

---

### Post by dmartinsca on 2006-12-05
The info you've posted doesn't really give much of an idea to diagnose the problem with tar. The error will be somewhere in the listing of files that scroll by, but it's not that tar is crashing so it just skips some files. You'd probably have better luck seeing what the trouble is if you don't use the -v (--verbose) flag. Chances are it's a file you don't have access to or a symlink to a file which doesn't exist anymore.

What type of storage is /dev/sda? External USB drive of some type, SCSI, or SATA? Whichever it is, have you had a look at dmesg right after boot to see if there are errors while trying to mount those drives? (Maybe the device nodes don't exist yet when the auto mounting is done?)

---

### Post by po0f on 2006-12-05
shane2peru,

Have you tried unmounting your data partitions before making the backup?  I know your tar command says to exclude them, but it might help.

Why don't you unmount /dev/sda1 and run e2fsck on it like dmesg suggests?

---

### Post by adamkane on 2006-12-05
You probably should use sbackup. It's a gui for tar, and it has scheduled backups.

---

### Post by Mimsy on 2006-12-05
You need to hit **ctrl-shift-c** when you want to copy from a terminal window. Ctrl-c has a completely different meaning, as you discovered.

My small contribution to the thread.

/Mimsy

---

### Post by dmartinsca on 2006-12-05
Or just highlight the text you want to copy then click the middle mouse button where you want to paste it. (Whenever i use windows I try to do this at least once before remembering i need to Ctrl+C & Ctrl+V)

---

### Post by shane2peru on 2006-12-06
> **dmartinsca said:**
> 
What type of storage is /dev/sda? External USB drive of some type, SCSI, or SATA? Whichever it is, have you had a look at dmesg right after boot to see if there are errors while trying to mount those drives? (Maybe the device nodes don't exist yet when the auto mounting is done?)

I have always used the v - verbose tag, I actually get that from the How to Backup and Restore thread right on these forums.  sda is an external USB drive.  Just a normal drive, it isn't sata.  It is an old laptop drive I had and put it in a case.  I have used it for a while very successfully.  I boot as little as possible, so I really don't know. Next time I reboot, I will try something like that.

[quote=po0f]
Have you tried unmounting your data partitions before making the backup? I know your tar command says to exclude them, but it might help.

Why don't you unmount /dev/sda1 and run e2fsck on it like dmesg suggests?[/quote]
actually I can't unmount them, since that is where all my storage is, I need to save to that partition.  The exclusions are links that I made to those drives for quick easy access.  I tried to run e2fsck, but I didn't know that it needed to be unmounted to run it.  Plus I really don't know how to run that command, and didn't want to mess things up worse.

[quote=adamkane]
You probably should use sbackup. It's a gui for tar, and it has scheduled backups.[/quote]
I have tried sbackup, and didn't really care for it.  I was working with the cli, because I want to put it in a crontab to run on a regular basis, that is why it has the fancy date format, I found that on the forums too.

[quote=Mimsy]You need to hit **ctrl-shift-c** when you want to copy from a terminal window. Ctrl-c has a completely different meaning, as you discovered.[/quote][quote=dmartinsca]click the middle mouse button where you want to paste it.[/quote]
Thanks, didn't know those tricks.  

Appreciate the help.  Thanks.

Shane

---

### Post by shane2peru on 2006-12-06
Shouldn't everything in /home/username theoretically be owned, and accessible by the username?  So if I tar it to backup, I shouldn't have to be root, correct?  When I run this as root, it works fine.   That doesn't make sense to me.  Thanks for the posts though.

Shane

---

### Post by po0f on 2006-12-06
shane2peru,

So is /media/storage symlinked to /home/shane/storage?  Your /etc/fstab entry for that partition doesn't contain a umask=000 option for mounting, just the /media/Portable entry.

---

### Post by shane2peru on 2006-12-06
> **po0f said:**
> shane2peru,

So is /media/storage symlinked to /home/shane/storage?  Your /etc/fstab entry for that partition doesn't contain a umask=000 option for mounting, just the /media/Portable entry.

Yep, you got it.  That partition is EXT3, so to my understanding (as limited as it may be) I don't think I need the umask - isn't that just for FAT32?  I'm the only user on this computer, and as many times as I have installed, I'm far less concerned about the security of my USB drive and has write access to it, I just want to use it all the time.  Hey!  My crontab just kicked in to back up my /home directory!!!  That is a plus! (this was just a test run to make sure it works.)  The issue of it not mounting at boot, is a problem because all my data is on the external, including my desktop background.  So theoretically when I boot, it should auto mount to get the desktop background, it always has in the past without a problem, just recently started being a pain!  Well tar fixed (that was user error, should be run in sudo).  And it did help to remove the -v option.  Now if we can fix my auto mount once again, we should be set.  Thanks.

Shane

---

### Post by po0f on 2006-12-06
shane2peru,

You could just mount /media/storage directly to /home/shane/storage instead of symlinking.  Also, after mounting it, see if changing the owner:group permissions on it helps:
```
[FONT="Courier New"]$ sudo mount -o user,auto /dev/sda1 /home/shane/storage
$ sudo chown shane:shane -R /home/shane/storage[/FONT]
```

And a shortcut to `date +%Y-%m-%d` is `date +%F`.  ;)

---

### Post by shane2peru on 2006-12-07
Hey, thanks, that is an easier way.  I think my auto mount in general is broken.  I plugged my card reader in, and a card, and it didn't auto mount.  I also turned on a second USB drive (my major backup one) and it didn't auto mount.  I don't think it is an ownership problem, as I'm about 90% sure that I have already changed the owner.  Is there a way to universally shut off and on the auto mount thing?  Somehow it has been switched to off.  When I put a CD in the drive and push it in, it doesn't even auto mount:confused:   It used to.  Maybe that was in Dapper it auto mounted?  I don't know, at any rate I appreciate the help.

Shane

Ok, forget all of this.  There was an update this morning, something about xorg etc.  I updated, and afterward re-booted, it didn't say I needed to, but I figure, if it has to do with xorg, it probably needs re-loaded for the changes to be applied.  When I rebooted, my background came right up!  So I inserted the CD, and it auto mounted.  I don't know what the problem was, but seems to be solved now.  Thanks for the help.  Oh, and just for the record here is my dmesg | tail right after I boot: ```
 dmesg | tail
[17179630.896000] Bluetooth: L2CAP socket layer initialized
[17179630.932000] Bluetooth: RFCOMM socket layer initialized
[17179630.932000] Bluetooth: RFCOMM TTY layer initialized
[17179630.932000] Bluetooth: RFCOMM ver 1.7
[17179631.664000] ath0: no IPv6 routers present
[17179631.740000] eth0: no IPv6 routers present
[17179632.512000] kjournald starting.  Commit interval 5 seconds
[17179632.512000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[17179632.528000] EXT3 FS on sda1, internal journal
[17179632.528000] EXT3-fs: mounted filesystem with ordered data mode.

```
Still gives warning about ext3 and e2fsck.  I guess I will have to search for that.

Thanks.
Shane

---

### Post by shane2peru on 2006-12-07
Ok, did the e2fsck thing.  All is working fine.  Thanks.  Also, po0f, there was a reason I didn't mount it in my home directory, but I don't remember what it is now.  I think it would actually be best to mount it under /mnt since I use it as a permanent drive, and that way it shouldn't show up on my desktop either.  I think I had problems with my user account and had to setup a new one, and switch everything over was a hassle.  That is why I decided to mount it under media. Thanks again for all the help.

Shane

---

### Post by po0f on 2006-12-07
shane2peru,

Glad you got it all sorted out with (some of) my help.  :)

---

