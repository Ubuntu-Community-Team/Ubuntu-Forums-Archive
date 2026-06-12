---
title: "Auto-mounted devices - owner reverting to root after reboot"
date: 2019-07-18
forum: General Help
---

### Post by shelzmike2 on 2019-07-18
This is quite puzzling and I have never seen it before. 

I have several partitions that I automount using fstab.  This is a new-ish build and am currently newly adding these partitions, mounting them, setting them up in fstab and then changing ownership from root to my user. When I do this, owner changes no problem; however, when I reboot, sometimes they revert back to root:root as the owner and I have no clue why. Any ideas?

---

### Post by TheFu on 2019-07-19
What file system is being used?
What is in the fstab file?
What are the permissions just after mounting? **ls -l** please.

---

### Post by shelzmike2 on 2019-07-19
ext4

fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=a9148939-dc74-4fd2-935a-5e597dd17222 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation - moved to /dev/sdc6 on 20190717
UUID=a2604894-ef10-42d3-8547-177ee543108a none            swap    sw              0       0


# Data Storage HDD
UUID=53e315fe-1bba-4151-a0c7-8501fa6f501e /media/DATA-HDD       ext4    defaults        0       2


# Synology Diskstation DS212j (Hostname: NAS-Diskstation)
UUID=8a0cf446-a4bc-4958-b885-566dcacc3acb /media/NAS-DISKSTATION        ext4     defaults,auto,_netdev 0 0


# Secondary Intel SSD used for rsync backups
UUID=4add5453-533d-4564-8902-02103d149600 /media/BACKUPS        ext4    defaults,auto,_netdev 0 0

```
Just after mount, shows root:

```
drwxr-xr-x  23 root root 4096 Jul 17 23:12 BACKUPS

```

Here is the really strange thing that I just discovered that may be a red herring and not related (purely coincidental), but when I first logged in just now, I had proper ownership, I then ran the following rsync (testing something else):

```
/usr/bin/rsync -aAXv --delete --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found","swapfile","/home/*/.thumbnails/*",".cache",".ecryptfs","/home/*/.local/share/Trash/*","/home/*/.cache/mozilla/*"} / /media/BACKUPS


```

I had to interrupt it because for some reason it was ignoring /media/ files as instructed in the command and I have no idea why. This isn't related to the ownership issue, but I did notice that right after I did this, I logged into the GUI and tried to delete the backup files it created and it wouldn't let me. Checked the ownership, and sure enough, it was back at root again!

---

### Post by shelzmike2 on 2019-07-19
I haven't yet tried it, but I am thinking that the part that I need to add to fstab are the options:

```
uid=1000,gid=1000
```

I will try this once everyone is in bed and not using the internet. This is my dns/dhcp server using dnsmasq and don't want to knock everyone off if the boot hangs :)

---

### Post by shelzmike2 on 2019-07-19
OK, well maybe that isn't exactly it. I rebooted before adding those options and the owner persisted... so now I am even more confused.

---

### Post by TheFu on 2019-07-20
uid/gid options should only be used for vfat/ntfs, not native Linux file systems.

Let's look at some of the issues. The original fstab
```
# Secondary Intel SSD used for rsync backups
UUID=4add5453-533d-4564-8902-02103d149600 /media/BACKUPS        ext4    defaults,auto,_netdev 0 0
```

Why is there a **_netdev** option for locally connected disks?  From the manpage:
```
       _netdev
              The filesystem resides on a device that requires network  access
              (used  to  prevent  the  system  from  attempting to mount these
              filesystems until the network has been enabled on the system).

```

Why use the **auto** option for directly connected storage?

I wouldn't place the mount points in /media/ either.  Lots of people do, but I've been burned doing that long time ago, and always avoid that area.

So, if you are willing, let's fix this.  Change the fstab to this:
```
UUID=4add5453-533d-4564-8902-02103d149600 /BACKUPS        ext4    defaults,noatime  0 2
```
Run some code .... 
```
sudo mkdir /BACKUPS   # Need an empty directory to mount.
sudo mount -a
```

Because it is backups, being owned by root makes perfect sense.  Backing up an OS, maintaining permissions is necessary, which would most likely be root:root for the / directory, so /BACKUPS will be reset to that no matter what.  I hope you are using sudo rsync -avz to make backups, BTW.  Permissions are critical to backups.

I'd never seen rsync groupings with {} before in my life.  Is that actually supported?  It isn't in the manpage.
```
Note also that the --filter, [B]--include, and --exclude options take  one
       rule/pattern  each[/B]. To add multiple ones, you can repeat the options on
       the command-line, use the merge-file syntax of the --filter option,  or
       the --include-from/--exclude-from options.

```

As for rsync, that really needs to be asked in a different thread were more people will see it.  I have my ways, but they are very different than what is shown.  And for backups, rsync usually isn't a very good tool.  I use **rdiff-backup** instead because it handles getting versioned backups, maintaining permissions as they change over time, and a few other things that backups need, which plain rsync doesn't handle.

---

### Post by shelzmike2 on 2019-07-20
The answer to all of your questions can be easily summed up by saying that all the reasons are because I am still learning and followed tutorials or guides on setting this up and didn't really look into what all the various options were, etc.!

Now that you mention it, I do understand why it probably does make sense to keep the owner as root on the rsync backup. 

To clarify about why I am using rsync. I am not actually necessarily looking for a backup in the truest sense of the word (i.e. with differential, as you mentioned). Instead, what I am really only after is a full system backup that I can get while the machine is running so that if my drive ever crashes I am not left trying to figure out how to build it all back up. I have it fine tuned to how I want it but it is not used for a personal computing system, so to speak. It is more for running services, such as dnsmasq for DNS/DHCP, some custom home automation stuff I have running, and Plex Media server, so not a lot of files changing that often. I chose to do it this way as I would have preferred to use RAID1, but I already have a running single-disk that does not have LVM, and I can't really find a definitive way to create the RAID. I also looked into converting to LVM, but also seems risky, quite involved. So asking myself "what is that that I really want here" I came to the conclusion that I just want a way to recovery the system fairly easily as this has bitten me recently and it sucked (meaning, NOT having a way to do it).

Good point about mounting to media as well. 

As far as rsync, indeed you can use '{..}' to combine all excludes and it does work when I run it manually, without issue. The problem, I found, is when I have a script that I have been trying to get to run automatically via a cron job placed in the daily folder. It seems to run once properly, but then the second time it runs, it ignores the /media exclusion and, well..it goes into an infinite loop which is no good. So, for now, I have removed it and will run it manually once a week until I can figure out a better way to automate it. I am thinking I will try to get it to work with a python script instead of a direct bash script. I want to add in some logging and email alerts on success/fail. 

I am using -av but not -z. I plan on only keeping 1 backup copy, and the drives are the same exact size and model, so didn't really see z being necessary. This is the only thing it will be used for. I have a larger drive to use for other things.

---

### Post by rbmorse on 2019-07-20
check the permissions of your read only partition from a terminal with 

```
ls -l
```

is there a little "+" at the end of the permissions line?  If it's there you might have an ACL issue.

---

### Post by TheFu on 2019-07-20
The original:
```
/usr/bin/rsync -aAXv --delete --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found","swapfile","/home/*/.thumbnails/*",".cache",".ecryptfs","/home/*/.local/share/Trash/*","/home/*/.cache/mozilla/*"} / /media/BACKUPS
```

The -A means to preserve both ACLs and permissions and owner/group .... so if / is owned by root:root, then so will /BACKUPS/ at the end of a proper rsync backup.  For local storage, using the -z option probably isn't needed.  I only do networked backups.
 
Use of ' instead of  " matters.  Shells can expand ", but don't touch '.
Third, if you have an encrypted HOME using .encryptfs, then that is only available when the userids are each logged in.  I found the home directory encryption unsuitable for that reason alone.
  
I have a plex server.  I use rsync for the media files with --delete, like you do.  But for everywhere else, I want real, versioned, backups, with rdiff-backup.

---

