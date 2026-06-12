---
title: "RAID 5 disks will not spin down"
date: 2014-04-09
forum: General Help
---

### Post by Tony_Lillie on 2014-04-09
I have Ubuntu 14.04 installed on a RAID 1 mirror and 4 separate disks in a RAID 5. I cannot get the RAID 5 disks to spin down. I've installed hdparm and edited the /etc/hdparm.conf file and added the following for each of the 4 disks ```
/dev/sdx {spindown_time = 242}
```

I also edited the /etc/default/smartmontools to stop smart from checking the disks every 30 minutes by adding the following ```
smartd_opts="-q never -i 7200"
```
[COLOR=#E6E0DB][FONT=Menlo]
[/FONT][/COLOR]They still do not spin down. So I tried the GUI method using the disk utility, and still no spin down. What can I do to get these disks to spin down?[COLOR=#E6E0DB][FONT=Menlo]
[/FONT][/COLOR]

---

### Post by Tony_Lillie on 2014-04-09
I just read a post that indicates mdadm monitoring could be the issue? I do have mdadm monitoring enabled and configured to send me emails, so maybe it is "pinging" the disks and keeping them awake.

I would use iotop to monitor a disk for a few minutes, but I can't get the data to stop scrolling in the terminal. How can I save the info collected by iotop in order to examine it and see what is "pinging" the disk?

---

### Post by frostschutz on 2014-04-09
I have mdadm (and smart) monitoring and my 7x HDD in a RAID5 spin down just fine (with LUKS, LVM and XFS on top).

It's usually the filesystem at fault, see if yours commits a journal regularly (ext* is notorious for this) and find a way to disable that. Also, obviously, check for any processes that access (read/write) files on the RAID.

If you use any kind of hibernate/suspend, the hdparm settings may be lost after wakeup if hdparm is not rerun explicitely.

---

### Post by Tony_Lillie on 2014-04-09
Ok, the info is coming in fast and furious now. Apparently my 4tb WD RED NAS drives do not support APM (advanced power management) which is needed for this automated spin down according to another post I read ughhh. So, I guess I will need to run a script of some kind using hdparm and the -y switch to turn them off.

I've never written a script like this. Anyone willing to help?

---

### Post by Tony_Lillie on 2014-04-09
So, I've learned a great deal in the past couple hours. The WD Red NAS drives have the same known issue as the Caviar Green drives with a head parking issue. I've disabled that function and created a script to run the hdparm -y function, but the cron job fails and I get a notification email telling me that "permission is denied". The cron job is trying to access the script in the /root directory where I created the /scripts directory, where the script file is located. So, apparently the cron job cannot access that folder. What can I do about that?

---

### Post by Tony_Lillie on 2014-04-09
Well, it seems I am my own best teacher tonight.

I gave the necessary permissions to the script file and the cronjob attempts to run, but it issues an error, "[FONT=arial]/root/scripts/disk_spindown.sh: line 10: hdparm: command not found"

Here is the script: ```
[/FONT]#! /bin/bash# Check for idle disks and spin them down


# Create a file on the ramdisk and cycle it to test for activity
( if [ ! -f /dev/shm/1 ] ; then touch /dev/shm/1 /dev/shm/2; fi ; mv /dev/shm/1 /dev/shm/2; cat /proc/dis$


# Loop through all array disks and spin down idle disks. Disks can also be written as {b..k}
for disk in {a b e f}
do
  if [ "$(diff /dev/shm/1 /dev/shm/2 | grep sd$disk )" =  "" ] ; then **hdparm -Y /dev/sd{abef};** fi
done
[FONT=arial]
```

I'm guessing something is wrong with the syntax of the portion I bolded, but I'm not sure. Anyone got any ideas.

I hate to go the self pity route, but it should be obvious that I'm really working hard to fix this and could really use some help.[/FONT]

---

### Post by Tony_Lillie on 2014-04-09
Beuller... Bueller...  ?? Anyone??

Well, I guess I can enjoy the fact that I did it all by myself!

The final issue was resolved by putting the complete /path/to/hdparm in the script. That immediately resolved the issue!

So, for those who only read the last post, I had to disable the head parking feature on the WD Red NAS drives by booting with a special version of UBCD found here: [http://www.mediafire.com/download/oag50v1qklpvn51/ubcd511custom.iso](http://www.mediafire.com/download/oag50v1qklpvn51/ubcd511custom.iso)

Though someday when that link is dead, you can build UBCD with the proprietary WDIDLE3.exe file and accomplish the same thing.

After disabling the head park, I created a script, gave its group and user read, write, and execute privileges with chmod, then created a cronjob to run the script every 120 minutes (2 hours). Based on the script, if the drives have not been read or written during that 2 hours, they will be put to sleep with hdparm -Y command.

Merely editing the hdparm.conf file will not work, because these WD Red NAS drives do not support APM (advanced power management).

This was really fun!! Seriously, I'm having a glorious little Linux moment and smiling from ear to ear. I LOVE LINUX!!

---

