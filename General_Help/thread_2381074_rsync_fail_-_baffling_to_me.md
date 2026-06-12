---
title: "rsync fail - baffling to me"
date: 2017-12-26
forum: General Help
---

### Post by sterator on 2017-12-26
I have made several successful rsync backups on my system (~10) but last night, when making what should have been a very quick backup - I'd done some work involving maybe 20mb worth of files, the backup proceeded as though it was the very first one!

I let the process go all night and woke to this:
No space left on device (28)
rsync error: error in file IO (code 11) at receiver.c(393) [receiver=3.1.1]

This makes zero sense: my backup is about 200gb, the destination drive is 500GB

the command I used to begin the rsync backup (including the final  / is this:
sudo rsync -azvv /home/phoenix/Documents /media/phoenix/Bento_Backup/

Also, I believe that I activated logging, but not sure where the log file would be deposited.

Can anyone explain how this rsync fail happened and how to fix it please?

**Edit:** also, when I do properties on my boot volume, it says that I have no free space..how can this be that the rsync command above worked fine, then suddenly not, and I think depositing a backup (which I don't see) on the boot volume?


**Edit 2:** maybe a clue here..looking for folders with a modification date of 12/25, I see the proc folder, when I get Properties, it says that the contents total 140.7TB, which is absolutely nuts. It's a 500 giga-byte drive.

So, if an rsync command is wrong, this is where things are deposited?

Thank you!

---

### Post by Holger_Gehrke on 2017-12-26
Sounds to me like the target drive wasn't mounted at the time of the backup and the files were written to the directory where the drive would be mounted, which would hide the (failed) backup when the drive is mounted and account for the missing space. 

The /proc directory is a pseudo-filesystem that gives (mostly read-)access to all kind of system internals, the size reported is completely spurious. If you try 'sudo du -c /proc' it will give you a size of 0 (zero!), which is closer to the truth, since there are no actual files in there and the contents of the files you see are generated when you access them.

Holger

---

### Post by sterator on 2017-12-26
> **Holger_Gehrke said:**
> Sounds to me like the target drive wasn't mounted at the time of the backup and the files were written to the directory where the drive would be mounted, which would hide the (failed) backup when the drive is mounted and account for the missing space. 

The /proc directory is a pseudo-filesystem that gives (mostly read-)access to all kind of system internals, the size reported is completely spurious. If you try 'sudo du -c /proc' it will give you a size of 0 (zero!), which is closer to the truth, since there are no actual files in there and the contents of the files you see are generated when you access them.

Holger

I remember seeing the target drive in a file manager window... could see the folders it contains, etc.
Is that not a good indicator of a drive being mounted?

Thank you!

---

### Post by #&amp;thj^% on 2017-12-26
> I remember seeing the target drive in a file manager window... could see the folders it contains, etc.
Is that not a good indicator of a drive being mounted?

Not Always...sometimes the Drives are just shown and not mounted. :)

---

### Post by oldfred on 2017-12-26
If path not identical to rsync's command then not mounted.

I did similar where I did not mount my /mnt/backup folder. And it almost filled / (root).
So now I include a mount in my bash file that run rsync.


```
# ! not 
if [ ! -d /mnt/backup ]; then
     mkdir /mnt/backup
fi
 
mount -t ext4 /dev/sdb5 /mnt/backup

```

I now create mount point as part of my install script so I know it exists.

So now it is more like this:

```
my_mount="/mnt/backup"
if grep -qs "$my_mount" /proc/mounts; then
  echo "It's mounted."
else
  echo "It's not mounted."
  mount -t ext4 /dev/sdb4 $my_mount
  if [ $? -eq 0 ]; then
   echo "Mount success!"
  else
   echo "Something went wrong with the mount..."
   exit $?
  fi
fi

```

---

### Post by The Cog on 2017-12-26
Look in /media/phoenix or look at the output of the command **lsblk**. It is possible that you already had a /media/phoenix/Bento_Backup directory when you plugged the drive in (this can happen if you don't unmount before shutdown for instance), in which case the drive could have been mounted on /media/phoenix/Bento_Backup_1.

---

### Post by sterator on 2017-12-26
I have some studying of these replies to do..thank you!

Can anyone tell me how to find the incorrect back up and properly delete it? It seems I have no free space on my boot volume - Thunderbird can't even create a temp file to send an email!

yikes!

:(

---

### Post by HermanAB on 2017-12-26
The df and mount commands (with no parameters) will give you a clue.

Delete some .gz files in /var/log to get some breathing room.

Umount the backup disk, check with mount and df that it really isn't mounted, then look in the usual mount point - if you see files there, then it wrote the data to the root.  Use rm -rf to remove the offending directory. 

(Never use .* as in Windows.  * includes a . already so .* would expand to .. which is the previous directory and then you delete your whole system)

---

### Post by oldfred on 2017-12-26
If /boot is full then that is where it went.

       # check sizes of 
Partition sizes
df -Th | grep sd| sort
Inodes:
 df -i
cd / or cd /home
sudo du -hc --max-depth=1
Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null
to also see hidden in /root folder
sudo du -sh /root/.[A-z]* /root/*

---

### Post by sterator on 2017-12-27
The Disk Usage Analyzer helped me to track down where the backup went. For me the pie visualizer is easier than the rectangles one, but I was able to see the backup and the size and get the analyzer to open the parent folder.

I was able to delete everything (send to trash, empty trash) except for the Bento_Backup folder - now empty - because I'm "not the owner and don't have the permission." 
Which seems weird, because rsync won't run w/o credentials.

And in a pleasant coinkystink, the FireFox bookmarks returned - as though the zero space left was preventing FF from getting at them.

Thank you for all of your suggestions. I'm pooped so prbly not a good idea to try rsync-ing at this time...time for spleep..

---

