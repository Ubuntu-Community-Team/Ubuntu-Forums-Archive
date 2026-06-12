---
title: "Why won't my hard drives spin down?"
date: 2008-03-26
forum: General Help
---

### Post by svenbertil on 2008-03-26
Having a problem getting my hard drives to spin down after some time of idle.

I've made a script that sets the timeout to 240 for the devices I've specified. Running the script produces no errors, output looks like this: (repeated for each device)
```

/dev/sdg:
 setting standby to 240 (20 minutes)

```


fstab is set to mount with defaults,noatime. Partitions are ext3 and xfs.

And here's the really strange thing, this morning I manually put one drive into standby with hdparm -y, and it's still sleeping, 7 hours later.

`uname -r`:
2.6.24-12-generic

There's currently one faulty drive in the system, sdc, so I get quite alot of these in my dmesg:
```

[376294.082108] Buffer I/O error on device sdc, logical block 0
[376294.082112] Buffer I/O error on device sdc, logical block 1
[376294.082114] Buffer I/O error on device sdc, logical block 2
[376294.082116] Buffer I/O error on device sdc, logical block 3
[376294.082127] sd 1:0:1:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[376294.082129] end_request: I/O error, dev sdc, sector 0
[376294.082130] Buffer I/O error on device sdc, logical block 0
[376294.082141] sd 1:0:1:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[376294.082143] end_request: I/O error, dev sdc, sector 0
[376294.082145] Buffer I/O error on device sdc, logical block 0
```
If that could have something to do with this issue?
I will get around to removing it, just always a bit reluctant to take that system down..

I suppose there is some way to tell from /proc or /sys what is actually going on and what is preventing my drives from spinning down, just I have no idea where to start looking.

---

### Post by tgalati4 on 2008-03-26
If the drive that refuses to sleep is the main drive then as long as there are system errors the log files will continue to be written to.  If it's a desktop machine, then I wouldn't worry about it.  For a laptop, you gain significant power savings with spin down, but also more wear due to spin-up.

You can search the forums for ways to reduce logging.  These techniques are used with USB flash drive installations, where you don't want excessive logging on a small, write-limited drive.

---

### Post by svenbertil on 2008-03-26
Thanks for replying, however it's not the system drive I'm having problems with. The system disks are included in my hdparm script but I don't expect them to actually spin down.

My script looks like this:
```
#!/bin/bash

DEVICES="/dev/sda /dev/sdb /dev/sdd /dev/sde /dev/sdf /dev/sdg /dev/sdi /dev/sdj /dev/sdk /dev/sdh /dev/sdl"

HDPARM=/sbin/hdparm

for DRIVE in $DEVICES; do
        $HDPARM -S 240 $DRIVE
done

```
(Yes I have that many disks in it.. :))

As stated above, if I manually put a drive in sleep with hdparm -y it stays that way, so I don't think it's disk activity (at least not in a normal sense) thats causing it.

---

### Post by svenbertil on 2008-03-27
I have now removed the faulty disk, dmesg shows nothing out of the ordinary going on with sd*, but my problem remains.

---

### Post by svenbertil on 2008-03-28
Further investigation has shown that it's the hddtemp daemon that prevents my drives from spinning down. In hddtemps manpage they state that one switch will activate hard drive spin up in order to read values, does anyone know of a way to reverse it? If I start hddtemp with my drives sleeping they spin up so it seems that de default is for hddtemp to wake drives up.

I know I've been using hddtemp in the past, no idea which version though, and have had no problems of this sort.

---

