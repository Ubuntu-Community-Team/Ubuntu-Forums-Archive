---
title: "Can someone help, issue with mount point versus directory with Back in Time backups"
date: 2020-06-27
forum: General Help
---

### Post by Ranbunta_Bantubunt on 2020-06-27
Howdy all. I am relatively new to using Linux (ubuntu) as my main OS. I love the concept of mount points, it's obviously super powerful. 

However I ran into an issue with back in time that kind of strikes at the heart of what is my residual confusion about how this works. 

I had an external device which I mounted at /media/user/NAME, and was backing up to it. To achieve this, I had to mkdir /media/user/NAME and then map an encrypted LUKS drive to that mount point and mount it.

Now the interesting thing is, the device was not connected to my machine, but back in time tried to back up to that directory anyway. So I wound up waking my computer and finding it to be out of disk space, with BIT having attempted to do a backup entirely into the local directly /media/user/NAME, without the media mounted.

This kind of is a central confusion for me. Is there a way to tell the file system to return an error if someone attempts to access /media/user/NAME and the device is not mounted? How would BIT be expected to know whether or not the "real" /media/user/NAME is mounted (the external device), as there is no circumstance under which I want /media/user/NAME to be accessed other than if that device is attached?

Or perhaps a solution from a different direction, perhaps I could tell BIT to use the device itself, eg, back up to a particular UUID, and not look for a particular directory? The "location" feature of BIT seems to depend on a directory path. 

Thanks for any tips! would be great to finally get the concept of how mount points and directories are supposed to co-exist happily :)

ranb.

---

### Post by oldfred on 2020-06-28
I filled my / once, I fortunately had enough room that it did not totally crash system.

I have an rsync script and added this to my script.
```

my_mount="/mnt/backup"
# ! not - moved to install script
#if [ ! -d /mnt/backup ]; then
#     mkdir /mnt/backup
#fi

# /dev/sdb4 backup_b partition on Z170, became sda4 with new NVMe drive
if grep -qs "$my_mount" /proc/mounts; then
  echo "It's mounted."
else
  echo "It's not mounted. Trying mount"
  mount -t ext4 /dev/sda4 $my_mount
  if [ $? -eq 0 ]; then
   echo "Mount success!"
  else
   echo "Something went wrong with the mount..."
   exit $?
  fi
fi

```

I also export list of installed apps into /home first so backup of /home includes latest list. I run bootinfoscript (now newest version part of Boot-Repair) to document system. And then rsync my data folders and /home.  I have several similar scripts for each flash drive that I also backup to. My "backup" to my other hard drive is not really a backup as it is just a copy at a point in time and will not include all the deleted files or history of changed files, just last version. But backups are on flash drives or external drives.

---

### Post by Ranbunta_Bantubunt on 2020-06-28
Nice idea. 

Also good to know I'm not just being dumb and missing something obvious with this issue :)

---

