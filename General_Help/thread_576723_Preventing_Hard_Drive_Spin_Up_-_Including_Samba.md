---
title: "Preventing Hard Drive Spin Up - Including Samba"
date: 2007-10-15
forum: General Help
---

### Post by danjl on 2007-10-15
Hi all,

Firstly, I don't know whether this is the right place to post.  Very sorry if not.  This is both a request for advice, and to provide hints to others trying to do the same thing as me.  The problem: a ubuntu box run as a server, for which I want to prevent ALL unnecessary hard drive spinups.  Especially overnight, when the system isn't doing anything.  But I still want services to run!

I have a sort of solution, but I want to see if there is a better one out there.  For those who want to know how to spin down their own drives, firstly you have to enable laptop mode to prevent unnecessary drive writes:

[http://ubuntuforums.org/showthread.php?t=96687]("http://ubuntuforums.org/showthread.php?t=96687")

However, inodes still get "dirtied", and the drive will need to spin up eventually.  Services such as SAMBA and logging will run, and wake the drive unnecessarily, regardless of the laptopmode settings.  It is very hard to trace down exactly how to prevent such logging.  I want to prevent all unneeded drive writes.

My solution is to create a number of ramdrives that are placed in the locations of the files that are being accessed.  You simply create the ramdrives on startup, copy the relevent files across, then copy the modified files back on shutdown.  This appears to solve the problem, although I have noticed that media playback is slightly less smooth that before, which I don't understand.

[B]
Questions:

1. Is there a better way to do this?  And are there any dangers I should be aware of?

2. At what point in the boot process would I insert my script?[/B]  I currently do it at xlogon - I'm sure it should be earlier but don't understand the boot process.

[I]For anyone else trying to silence their machine, I include the references:

To see which files are being accessed and causing the problem:

[http://www.jenitennison.com/blog/node/51]("http://www.jenitennison.com/blog/node/51")

My script to create the ramdrives looks like this:
> #!/bin/sh
# Doing this using ramdisks.  However, tmpfs might be better:
# mount -t tmpfs tmpfs /mnt/tmpfs -o size=100M
# 

drivelist="/home/mythtv/ramdrives.txt"
ramdrive="/mnt/rd"
ramdev="/dev/ram"

numdrives=`cat $drivelist | wc -l`
rd=0
while [ $rd -lt $numdrives ]; do
    file=`head -n $((rd+1)) $drivelist | tail -1`
    curdrive=$ramdev$rd
#   echo $file: $curdrive
    mke2fs -m 0 $curdrive
    mount $curdrive $ramdrive
    cp -rp $file/* $ramdrive
    umount $ramdrive
    mount $curdrive $file
    rd=$(($rd+1))
done
#echo $file
#mke2fs -m 0 /dev/ram0
#mount /dev/ram0 $ramdrive
#cp -r $file $ramdrive

chown mythtv:root /var/cache/freevo

With /home/mythtv/ramdrives.txt containing:
> /var/cache/samba
/var/run/console
/var/log
/var/cache/freevo

Finally, the shutdown script:
> #!/bin/sh
# Doing this using ramdisks.  However, tmpfs might be better:
# e.g. mount -t tmpfs tmpfs /mnt/tmpfs -o size=100M
# 

drivelist="/home/mythtv/ramdrives.txt"
ramdrive="/mnt/rd"
ramdev="/dev/ram"
tmpdir="/tmp/rd"

mkdir -p $tmpdir 

numdrives=`cat $drivelist | wc -l`
rd=0
while [ $rd -lt $numdrives ]; do
    file=`head -n $((rd+1)) $drivelist | tail -1`
    curdrive=$ramdev$rd
    rm -r $tmpdir/*
    cp -rp $file/* $tmpdir
    umount $file
    cp -rp $tmpdir/* $file
    rd=$(($rd+1))
done
#echo $file
#mke2fs -m 0 /dev/ram0
#mount /dev/ram0 $ramdrive
#cp -r $file $ramdrive

chown mythtv:root /var/cache/freevo

[/I]

---

### Post by danjl on 2007-10-21
OK, I found an answer elsewhere, of sorts.  For everyone else looking for a solution:

You put the script to create a tmpfs log file into the /etc/rcS.d folder to have it run on boottime.

There is a better script than mine, and a step by step guide, at:

[http://forums.debian.net/viewtopic.php?t=16450&start=0&postdays=0&postorder=asc]("http://forums.debian.net/viewtopic.php?t=16450&start=0&postdays=0&postorder=asc")

Daniel

---

