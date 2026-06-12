---
title: "Syncoid rpool issue"
date: 2023-12-12
forum: General Help
---

### Post by aljames2 on 2023-12-12
In testing to try out Syncoid to send a copy of my ZFS rpool & snapshots to a separate local internal storage device, I ran in to an issue, I think..

The first run of the command worked fine.  The second run the following day also went fine.  Today I ran it and my target: /zfs-backups/rpool/ is showing empty.

```
syncoid -r rpool bckpool/BACKUPS/ubuntu_2204/rpool --no-sync-snap
```

When I ran the command today it produced normal output on my screen like I was expecting, but the directory is showing empty.

When I check /zfs-backups/rpool/.zfs/snapshot$   there is a list of autosnap directories but they are all showing empty.

It must be something simple.

EDIT:
I rebooted the machine and now the directory is showing data.  Not sure why things would go invisible until a reboot.  It is hard for me to determine if this is all working properly.  when I look at the autosnap dates & times, it shows my latest one being 12/13 which is tomorrow, not here yet :)
Must be a timezone thing or something.

---

### Post by MAFoElffen on 2023-12-13
Not sure. I don't know how Sanoid and Syncoid gets their dates. I do know he has this note on his GitHub, right after an example cron line
```

* * * * * TZ=UTC /usr/local/bin/sanoid --cron
     
# Note: Using UTC as timezone is recommended to prevent problems with daylight saving times

```
I am presently writing my own scripts to do the same things, but as sort of full recursives, then incremental backups of the same.

---

### Post by aljames2 on 2023-12-13
My goal is to automate with a script & cron the incremental syncs using syncoid, or zfs send (haven’t tried zfs send yet).  I’m just not sure yet if it is working correctly, because the dates are throwing me off.  I have sanoid maintaining the most recent 30 hourlies, 14 daylies, & 3 monthlies, all while auto-purging the oldest.

When I run the date command it gives me the correct date & time including timezone.

---

### Post by #&amp;thj^% on 2023-12-13
Locally i use something along the lines of, and this is very generic, so tweak it to your needs:
```

sudo zfs send -R storage/photos@frequent_2023-02-12_18:15 | \
       pv | ssh example.com "cat - > zfs-pipe"
```

pv is optional of course. I find it nice to have something to watch for progress.

BUT for this to work, SSH into the remote server and run:
```

mkfifo zfs-pipe

# It doesn't ask for your password until the pipe starts to receive 
# data. So check back here when you start the local command
sudo zfs receive storage/photos < zfs-pipe 
```

After done and I'm a neat freak so I remove the zfs-pipe filter.
One less thing to trace if something mucks-up.
Sorry I don't use syncoid, but i know some who dose. ;:

---

### Post by MAFoElffen on 2023-12-13
Sanoid/Syncoid uses ZFS Send...

If you are using that, that will do what you want, and not get confused with itself. As long as you stay consistent. Doing that with cron will ensure you stay consistent.

---

### Post by aljames2 on 2023-12-13
Thank you both, I’ve got my syncoid script on a cron and will keep an eye on it.

I wouldn’t normally try to replicate all of root on my other filesystems but since a root zfs install is not a 15 minute process it seems good to have the ability to go back to a prior state if needed.  Also, good for restoring vms when needed.

Currently my real backup server is ext4+Lvm, so I want to also play around with some rdiff-backup pulls of some data configs, scripts, and such off this zfs system.  I’ll set up a new LV for that in case something goes haywire.

---

### Post by aljames2 on 2023-12-14
> **aljames2 said:**
> 
EDIT:
I rebooted the machine and now the directory is showing data.  Not sure why things would go invisible until a reboot. 

All my mountpoints in my backup pool show empty after running syncoid but the datasets all appear to be mounted.  As I mentioned in my OP, a reboot brings them back into view.  I tried today doing just a manual export & import of my backup pool instead of rebooting and that also brings back the pool.

Could it be that one would need to do:
```

sudo zpool export bckpool
sudo zpool import bckpool

```

after each syncoid run?  I could include this in my backup script the only problem with that I could see is if there is a failed export which happens from time to time if the system thinks something is in use... maybe force the export?  Perhaps leave it alone and it will just continue to backup like normal even though I can't see folder contents until a manual pool refresh.  My system stays on 24/7.

---

### Post by #&amp;thj^% on 2023-12-15
Remember COW lies until a change is made, it will or should be there regardless of what's shown.
Just roll with the flow all will be revealed to those who are patient. :D

---

### Post by aljames2 on 2023-12-16
> **1fallen said:**
> Remember COW lies until a change is made, it will or should be there regardless of what's shown.
Just roll with the flow all will be revealed to those who are patient. :D

Will do, that makes sense.  

I also figured out that my target pool for syncoid backups has all the child datasets unmounted when I would check the next day.  Everything is mounted after a manual reboot, or export/import, but for some reason these locations become unmounted again after the next days syncoid run. I can't confirm syncoid is the cause though yet.

I check for what is mounted using:
```
zfs get mounted -r bckpool
```

I see the lower level mounts are not persisting.  I can do
```
sudo zfs mount -a
```

and everything is mounted again.

---

