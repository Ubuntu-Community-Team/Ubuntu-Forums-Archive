---
title: "rsync incremental backups which delete old backups"
date: 2015-08-18
forum: General Help
---

### Post by funkytwig2 on 2015-08-18
Hi, came across a great article on how to do backups like apple Timemachine.

[https://blog.interlinked.org/tutorials/rsync_time_machine.html](https://blog.interlinked.org/tutorials/rsync_time_machine.html)

It revolved around 
```
rsync -aP --link-dest=PATHTO/$PREVIOUSBACKUP $SOURCE $CURRENTBACKUP

```

And did do the incremental backup  but how about deleting old backups when the drive gets full.  If my understanding is correct deleting old backup directories is OK because the hard link is kept until the last file using to it is deleted. I think what I needs to be done at the beginning of the script is something like:
```


while drive is almost full[INDENT]delete oldest backup directory[/INDENT]
end while



```

Almost full will be a percentage, any advice/code snippets on this would be great.

I am planing on doing hourly backups but at the end of the day (or maybe the beginning of the next day) delete all but one backup for the day.

Lastly every month I would like to create a monthly backup and delete all the backups more than a month old.  For this it seems the best thing to do is is copy the whole file structure of the last backup into a directory with a special name (maybe I start directory name on hourly with H-, daily with D- and monthly with M-).  The rub here is I want to do it with hard links so I dont end up using lost of disk space.  I am thinking
```
cp -al dirA dirB
```

Would be the way to go?

All advice gratefully reverenced.

Ben

---

### Post by TheFu on 2015-08-18
Versioned backups are important.

**back-in-time** manages hard-link backups and uses the same hardlinks in the solution. It is very much like the Mac solution.

There are some issues with hard-link backup solutions - as permissions change over time, those are lost. Tools based on **duplicity** or **rdiff-backup** don't have those issues, but work in a slightly different way.  Duplicity has all the best-practice features, but it isn't perfect. It behaves more like old-school backups with weekly fulls and daily incremental backups. This is similar to the old dump/restore techniques. rdiff-backup is a hybrid - like rsync for the most recent backup and compressed differences for all older backup versions. Permissions for each revision are maintained. [https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/) is a nice intro.

All of these tools have build-in options to clean up old backups.

Oh - and if you want to stay with a more manual backup solution close to rsync - check out rsnapshot - it is a well-know script around rsync. I think it has been put in a few books.

Don't forget to test the restore for whatever method you go with. Backups are 10% of the solution. The other 90% is the actual restore.

---

### Post by papibe on 2015-08-18
Hi funkytwig2.

Here a couple of similar threads where you can grab some examples: [here]("http://ubuntuforums.org/showthread.php?t=2287961&highlight=rsync") and [here]("http://ubuntuforums.org/showthread.php?t=2286156&highlight=rsync").

I also recommend taking a look at standard backup tools.  TheFu's examples are an excellent start.

Having said that, here are some thoughts:
[LIST]
[*]I would define a limit on the disk usage, so both backup time (writes), and restore time (read) won't slow to a crawl.
[*]I'd check how full the disk is in the script itself, instead of creating another script.
[/LIST]
For instance, this could be at the end of the script:
```

MAX_USAGE=80       # 80% full, or 20% of free space.
PATH_TO_BACKUPS="/path/to/backups/"

# Get current disk usage.
temp="$(df --output=pcent "$PATH_TO_BACKUPS" | tail -n1)"
current_usage="${temp/\%/}"

if [ "$current_usage" -gt "$MAX_USAGE" ]; then
    echo "Disk usage above limit."
    echo "Removing old backups."
    ...
else
    echo "Disk usage below limit."
    echo "Leaving old backups as they are."
   ...
fi

```
Hope it helps. Let us know what you think.
Regards.

---

### Post by funkytwig2 on 2015-08-18
Thanks for the replies.  The advantage of the 'mac like' backups, although saying that is very loaded language, they are actually very user friendly as they allow for human error to be easily rectified by non technical humans.  This is a very small charity and there is no on-site support.

The context for this is there is a NAS with a 2GB and 4TB drive.  The 4TB drive is the incremental roll back style backup.  All the client machines are windows.  Basicaly the idea is the clients can restore stuff themselves, hence the rsync thing as if the directories sensibly named  it is user friendly.  There is also a off site backup over VPN.  Now it may be better to have the NAS simply mirror and the offsite to hold the incremental roll back style backups.  In fact now I think of it this is a very good idea.  We were originally going to use Gene9 Genuine timeline for the backups but it apparently does not like working over a VPN.

What I liked about the resyn method is the restores are platform agnostic as its just a directory structure.  

The main things are 1) the users need to be able to do the restore from there windows computers and 2) the incremental backup drive is only twice the size of the main drive (they don't change loads of data a day, mainly documents and adding photos, and maybe the odd video.

I as re-purposing an old desktop for Linix, mainly just to run the resync stuff.

---

### Post by TheFu on 2015-08-19
> **funkytwig2 said:**
> Thanks for the replies.  The advantage of the 'mac like' backups, although saying that is very loaded language, they are actually very user friendly as they allow for human error to be easily rectified by non technical humans.

<snip>

I as re-purposing an old desktop for Linix, mainly just to run the resync stuff.

**Back-in-Time** is what you want then. Do that local to the LAN.
Then use rsync of those areas offsite. I'm not exactly how to do this retaining hardlinks, but there must be away.  Since we've been using rdiff-backup, normal rsync to off-site just works. No hardlinks.  

With rdiff-backup, the most recent backup is a mirror and available to end users just like with rsync/back-in-time - just be certain to mount backup storage areas read-only so they don't delete their files there too!

---

### Post by funkytwig2 on 2015-08-26
OK, I think I have cracked it.  Have done a set of scripts and have done a blog posting with them at [http://www.funkytwig.com/blog/funkybackup](http://www.funkytwig.com/blog/funkybackup).  In someways it is better than Timemachine as it enables backups  to be done several times an hour.

The off-site backup will be done using a VPN.  The offsite location will have a Raspberry Pi ruining the scripts and I will have read only versions of the backup directories via Samba.

Be good if people could have a look and give feedback.

---

### Post by TheFu on 2015-08-26
Seems like your script (based on skimming the blog only) does what BackInTime does. [http://backintime.le-web.org/](http://backintime.le-web.org/)  It has existed for many years and has been well-tested.

Raspberry Pi's aren't know for their network or disk I/O.
Samba sharing loses the permissions and may make certain files which should NOT be generally available, available. For example, certain credentials should never be available just to anyone.

Why bother with a VPN?  Just use rsync, which uses ssh-tunnels by default. No need to have double-encryption, IMHO.

OTOH, a little script like this can be fun to make and if it works for you, great!

Please use the Thread-Tools to mark this thread as "SOLVED" to help others.

---

