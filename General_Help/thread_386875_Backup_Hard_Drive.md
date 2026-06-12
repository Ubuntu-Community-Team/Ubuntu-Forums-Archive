---
title: "Backup Hard Drive"
date: 2007-03-17
forum: General Help
---

### Post by dontgetshocked on 2007-03-17
I am looking for a utility to backup the os just in case so I can do a restore, i.e. image the os and boot from the cd or dvd and re-install.

Thanks,

---

### Post by AtrejuT on 2007-03-17
rsync is a very neat tool, it also allows you to do incremental backups and all kinds of fancy stuff. I have a script using rsync to make weekly incremental backups oh my homefolder to an external HD - it's really simple:

```

rsync -arlpt --progress --delete --delete-excluded -h --exclude-from=.exclude --backup --backup-dir /media/disk/backups/`date +%W`/ /home/atreju /media/disk/backups/ 

```

the external HD is mounted to /media/disk it will backup everything in /home/atreju except the things listed in a file .exclude and it will save all weekly changes to /media/disk/backups/*numberofweek*/, so I have a complete history of weekly snapshots for a year. After that year it starts overwriting the weekly folders.
You can probably adapt this for your purpose.

atreju

---

### Post by ardchoille42 on 2007-03-17
I use partimage to back up my / partition, it takes about 10 minutes to back up a 3.5Gb partition and compresses it down to about 900Mb. I then burn that image to a DVD for safekeeping. I recently had to restore my / partition from a recent image and the restore took about 8 minutes and I found that partition was just as I had left it - the backup and restore worked perfectly. PartImage is a perfect backup strategy when you are talking about entire partitions.

The partimage homepage is [here]("http://www.partimage.org/Main_Page").

Also, there is a nice livecd that has partimage on it, along with a lot of other admin tools, and I recommend this livecd to everyone. You can get the System Rescude CD [here]("http://www.sysresccd.org/Main_Page").

Yes, partimage is in the repos, but you need to run it on a partition that isn't mounted for it to work. This is why I recommended the System Rescue CD.

---

### Post by floke on 2007-03-17
You could try partimage.
A good guide can be found here,
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by buuntuu! on 2007-03-17
and there's always the [command line approach]("https://help.ubuntu.com/community/BackupYourSystem/TAR?highlight=%28system%29%7C%28backup%29") ;)

---

### Post by skyttan on 2007-08-20
But how can I backup whole hard disk? Like now I am switching to a bigger but don't want to lose ANY configuration or document.

---

