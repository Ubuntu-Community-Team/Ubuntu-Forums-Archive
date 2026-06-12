---
title: "Backup Solution with auto-delete of oldest backup when destination full."
date: 2016-01-30
forum: General Help
---

### Post by Zorrokan Zenovka on 2016-01-30
Hi

I've been playing around with rsync and bash scripting to create a command line / scripts based backup solution.  One thing my script-fu isn't good enough for yet however is the auto-deletion of the oldest backup from the target disk once it exceeds a certain volume.

As I'm running short on time now to complete this project, I've been looking at FOSS off the shelf backup solutions (some based on rsync some not, it isn't essential) and I'm having difficulty identifying one that would provide that function.

Also, the backup solution should not only be capable of making full daily backups to a directly attached HDD (for ease and speed of restoration should the need arise), but also it should send an incremental backup offline.  Easy enough to identify solutions that do that... but auto-delete of oldest backup when target disk gets full?

Anyone?

thanks


zz

---

### Post by Zorrokan Zenovka on 2016-01-30
Nevermind!

Think I found the answer to my scripting in the head command/utility.

#!/bin/bash

## Delete oldest backup if target disk more than 95% full. 
diskused=$(df -BM /dev/sdx | sed 1d | cut -d' ' -f28 | cut -c 1)
oldestfolder=$(ls /home/jerk/backups | sort | head -n1)
	while [ $diskused > 95 ]
	do 
		rm -fr /media/localbackup/"$oldestfolder"
	done

## create a directory with todays date as its name and rsyncs all system and data over to it
todaysdate=$(date +"%Y%m%d")
rsync -aAXv --exclude={"/dev/*","/tmp/*","/proc/*","/sys/*","/run/*","/media/cdrom/*","/lost+found/*","/media/localbackup/*"} / /media/localbackup/$todaysdate

May need a little work on the exact syntax to get it to work (I am not in the position to test atm). but essentially I think that's it.

---

