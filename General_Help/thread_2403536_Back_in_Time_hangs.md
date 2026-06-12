---
title: "Back in Time hangs"
date: 2018-10-12
forum: General Help
---

### Post by VanillaMozilla on 2018-10-12
Back in Time worked very simply and quickly on a small backup job with a few GB.  On a bigger job (>400 GB) it fails completely.  It reads the hard drive continuously, but does not write data.

1. backintime-qt4 does nothing.  I add some directories and specify the destination USB drive.  When I press <OK>, nothing happens.

2. Back in Time (root) (pkexec backintime-qt4) starts two instances of rsync.  This uses a lot of CPU time andreads the hard drive continuously, but it doesn't write anything.  The hard drive drive light will stay on continuously for hours, but df shows nothing being written on either drive.  I then ended all rsync and backintime processes with System Monitor.

If I restart the GUI, BIT has remembered the configuration, including file lists and target drive, but the terminal says files not found.  (And it's no wonder files were not found, because it didn't write them.

The terminal output shows some inscrutable error messages.  I'll post them in a followup message.

Two questions, obviously:  What's wrong and how can I get my backup?

---

### Post by VanillaMozilla on 2018-10-12
Other info:  Ubuntu 16.04 flashback (or fallback?), 32 bits.

There are some errors that I haven't been able to decypher, including "rsync ...returns 5120".  By default it's set to continue after errors.  I just set it to back up a few top-level folders--nothing complicated that I know of.

Terminal output:

~$ pkexec backintime-qt4

Back In Time
Version: 1.1.12

Back In Time comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions; type `backintime --license' for details.


Back In Time
Version: 1.1.12

Back In Time comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions; type `backintime --license' for details.

INFO: Lock
INFO: Take a new snapshot. Profile: 1 Main profile
INFO: Call rsync to take the snapshot
"sni-qt/9340" WARN  15:18:35.261 void StatusNotifierItemFactory::connectToSnw() Invalid interface to SNW_SERVICE 
INFO: [qt4systrayicon] begin loop
WARNING: Command "rsync -rtDHh --links --no-p --no-g --no-o --info=progress2 --no-i-r  --delete --delete-excluded  -v  --chmod=Du+wx  --exclude="/media/MyHome/TOSHIBA EXT" --exclude="/root/.local/share/backintime" --exclude=".local/share/backintime/mnt" --include="/home/MyHome/Documents/" --include="/home/MyHome/" --include="/home/" --include="/home/MyHome/Music/" --include="/home/MyHome/Pictures/" --include="/home/MyHome/ProgramFiles/" --include="/home/MyHome/Videos/" --exclude=".gvfs" --exclude=".cache/*" --exclude=".thumbnails*" --exclude="[Tt]rash*" --exclude="*.backup*" --exclude="*~" --exclude=".dropbox*" --exclude="/proc/*" --exclude="/sys/*" --exclude="/dev/*" --exclude="/run/*" --exclude="/etc/mtab" --exclude="/var/cache/apt/archives/*.deb" --exclude="lost+found/*" --exclude="/tmp/*" --exclude="/var/tmp/*" --exclude="/var/backups/*" --exclude=".Private" --include="/home/MyHome/Documents/**" --include="/home/MyHome/Music/**" --include="/home/MyHome/Pictures/**" --include="/home/MyHome/ProgramFiles/**" --include="/home/MyHome/Videos/**" --exclude="*" / "/media/MyHome/TOSHIBA EXT/backintime/Opal/root/1/new_snapshot/backup/" 2>&1" returns 5120

<Here I terminated 3 instances of rsync>

INFO: Save config file
INFO: Save permissions
INFO: Create info file
INFO: Remove backups older than: 20081001-000000
INFO: Keep min free disk space: 1024 MiB
INFO: Keep min 2% free inodes
INFO: Unlock
INFO: [qt4systrayicon] end loop
Terminated

---

### Post by VanillaMozilla on 2018-10-12
Solved, I think.

It was a matter of getting it to accept the right target drive.  There were different drives with subtly different names.  I had some difficulty in getting it to accept the right name, but I don't know if I can duplicate the problem.  It's running right now and appears to be all right.

---

