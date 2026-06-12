---
title: "My Backup script using rdiff-backup and an external usb hd"
date: 2007-02-08
forum: General Help
---

### Post by brad.m.sims on 2007-02-08
Any comments or improvements are of course most welcome.

I use this at least weekly, the only changes I needed to make for
ubuntu vs debian was commenting out the mount commands and 
changing the mountpoints...

It saved my bacon when I had a disk failure not too long ago.

```

#!/bin/bash

#-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-#
                                ##Script Variables##

        # Backup device #
# Variables used to specify the backup device
# and mount point to use
       # Not needed on Ubuntu, automount actually works.
#BACKUP_DEVICE="-t ext3 /dev/sdg1"
MOUNT_POINT="/media/usbstick"

        # Sources to backup #
# Directory/specific files to backup.
SOURCES="/"
# If you need to specify more than a single path, comment
#  out the line above and edit the following accordingly:
#SOURCES="--include-globbing-filelist /path/to/include/file"

        # Target Directory #
# Directory to backup to. This is where your backup(s) will be stored.
# Exclude trailing slash!
TARGET="/media/usbstick/rdiff-backup"

        # Exclude File #
# Your EXCLUDE_FILE tells rsync what NOT to backup. Leave it unchanged if you want
# to backup all files in your SOURCES. If performing a FULL SYSTEM BACKUP, ie.
# Your SOURCES is set to "/", you will need to make use of EXCLUDE_FILE.
# The file should contain directories and filenames, one per line.

# An example of a EXCLUDE_FILE would be:
# /proc/
# /tmp/
# /mnt/
# *.SOME_KIND_OF_FILE

EXCLUDE_FILE="/home/bsims/Scripts/Backup/exclude_file.txt"

        # Extras #
#       If these extras are not wanted comment out
#       the script extras section

# I wanted a log of when this script was last ran...
#  this specifies the path and name to use
HISTORY_LOG="/home/bsims/Scripts/Backup/Backup_History.txt"

# I run Ubuntu and a list of installed packages is useful
#  if one needs to reinstall
DPKG_LIST="/home/bsims/Scripts/Backup/dpkg-filelist"

#-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-#
                                   ## Verify Device and Sources ##
# Not needed on ubuntu, automount actually works.
# We need to mount the external usb HD
        #echo " Mounting External USB Drive... "
        #sudo mount $BACKUP_DEVICE $MOUNT_POINT

        #echo " Done."
        #echo " "
        echo " Starting backup..."

# -x returns true if the file exists and is executable.
        if [ ! -x $TARGET ]; then
                echo " Backup target does not exist or you don't have permission!"
                echo " Exiting..."
                exit 2
        fi

        echo " Verifying Sources..."
                for source in $SOURCES; do
        echo " Checking $source..."
                if [ ! -x $source ]; then
        echo " Error with $source!"
        echo " Directory either does not exist, or you do not have proper permissions."
                exit 2
        fi
        done

# -f returns true if the file exists and is a regular file.
        if [ -f $EXCLUDE_FILE ]; then
        EXCLUDE="--exclude-globbing-filelist $EXCLUDE_FILE"
        fi
                           ## Actual Backup ##
echo " Sources verified. Running rdiff-backup..."
echo " "
echo " This may take a while..."
echo " "
echo " May I suggest a nice cup of coffee "
echo " while you are waiting?"
echo " "

        sudo rdiff-backup -v5 --print-statistics $EXCLUDE $SOURCES $TARGET

                           ## Script Extras ##
# I want a log of when I last ran this script, and a list
# of every package installed on my computer.

        date +'%F_%H:%M'>> $HISTORY_LOG
        dpkg -l | awk '{print $2}' > $DPKG_LIST

                           ## Disc Information ##
# I want to know how much space I have left
echo " "
echo " Displaying Drive Information:"
        df -h

echo " "
                        ## Unmount Backup Device ##
 #Now we have to umount this beast before we can remove it...

echo " "
echo " Unmounting External USB Drive from /Backup..."
        sudo umount $MOUNT_POINT
echo " Done."
echo " It is now safe to shutdown and/or remove the external USB drive."
        exit 0

```

---

### Post by ofir_k on 2007-02-08
brad.m.sims:
Thanks for the great script!!!

Right now I am backing up the system and maybe it will help me.

Anyway, thanks again for the script.

---

### Post by brad.m.sims on 2007-02-08
> **ofir_k said:**
> brad.m.sims:
Thanks for the great script!!!

Right now I am backing up the system and maybe it will help me.

Anyway, thanks again for the script.

You are most welcome, I posted it to be used.

---

### Post by scott_b on 2007-03-08
I copied your script, edited it for my sys, and made it executable.  but when I create an exec called rdiff-backup it just seems to go in loops.  

I'm sure you'll get a good laugh out of it, but could you give me a hand?

---

### Post by scott_b on 2007-03-08
holy freaking cow - blithering idiot

apt-get rdiff-backup
 
*sigh* how embaricing

---

### Post by Edk on 2007-03-13
I am still strugging to get this to work!

I have a NAS that is easily accessed by the rest of my Ubuntu system.

I have mounted it thus:
sudo mount -t smbfs //192.168.1.18/data /mnt/backup -o username=unpassword,password=pwpassword,fmask=0777,dmask=0777

This works fine

When I try to run rdiff (or the GUI KEEP ) I get a MASS of error messages:-

Exception '[Errno 1] Operation not permitted: '/mnt/backup/DadsLinux/rdiffbu'' raised of class 'exceptions.OSError': File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 295, in error_check_Main try: Main(arglist) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 315, in Main take_action(rps) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 271, in take_action elif action == "backup": Backup(rps[0], rps[1]) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 324, in Backup backup_set_rbdir(rpin, rpout) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 381, in backup_set_rbdir rpout.chmod(0700) # just make sure permissions aren't too lax File "/usr/lib/python2.4/site-packages/rdiff_backup/rpath.py", line 826, in chmod self.conn.os.chmod(self.path, permissions & Globals.permission_mask) Traceback (most recent call last): File "/usr/bin/rdiff-backup", line 23, in ? rdiff_backup.Main.error_check_Main(sys.argv[1:]) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 295, in error_check_Main try: Main(arglist) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 315, in Main take_action(rps) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 271, in take_action elif action == "backup": Backup(rps[0], rps[1]) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 324, in Backup backup_set_rbdir(rpin, rpout) File "/usr/lib/python2.4/site-packages/rdiff_backup/Main.py", line 381, in backup_set_rbdir rpout.chmod(0700) # just make sure permissions aren't too lax File "/usr/lib/python2.4/site-packages/rdiff_backup/rpath.py", line 826, in chmod self.conn.os.chmod(self.path, permissions & Globals.permission_mask) OSError: [Errno 1] Operation not permitted: '/mnt/backup/DadsLinux/rdiffbu'

Can anyone tell me what I am doing wrong!

Thanks


Ed

---

### Post by brad.m.sims on 2007-03-14
> **Edk said:**
> I am still strugging to get this to work!

I have a NAS that is easily accessed by the rest of my Ubuntu system.

I have mounted it thus:
sudo mount -t smbfs //192.168.1.18/data /mnt/backup -o username=unpassword,password=pwpassword,fmask=0777,dmask=0777

This works fine

When I try to run rdiff (or the GUI KEEP ) I get a MASS of error messages:-

Can anyone tell me what I am doing wrong!



Are you running this as root?

---

### Post by Edk on 2007-03-14
No,  I am not.  

I tried it, and got the same mass of error messages, but I noticed at the end that it said, 

[INDENT]OSError: [Errno 2] No such file or directory: '/mnt/backup/DadsLinux/rdiffbu/rdiff-backup-data/rdiff-backup.tmp.0/5-[/INDENT]_ a.'

I am trying to backup to /mnt/backup/DadsLinux/rdiffbu/

Thanks for having a look at this for me


Ed

---

### Post by brad.m.sims on 2007-03-15
> **Edk said:**
> No,  I am not.  

I tried it, and got the same mass of error messages, but I noticed at the end that it said, 

[INDENT]OSError: [Errno 2] No such file or directory: '/mnt/backup/DadsLinux/rdiffbu/rdiff-backup-data/rdiff-backup.tmp.0/5-[/INDENT]_ a.'

I am trying to backup to /mnt/backup/DadsLinux/rdiffbu/

Thanks for having a look at this for me


Ed

No idea, sorry

---

