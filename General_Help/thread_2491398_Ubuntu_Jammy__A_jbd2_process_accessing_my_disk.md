---
title: "Ubuntu Jammy : A jbd2 process accessing my disk"
date: 2023-10-07
forum: General Help
---

### Post by georgesgiralt on 2023-10-07
Hello Guys,
I use a laptop SATA drive to make backups. It is accessed through an SATA/USB interface on my laptop. 
I normally create a new file system on this drive and do a dump/restore backup. 
```

mkfs.ext4 -m 0  -j -L home  /dev/sde1
mount /dev/sdc1 /mnt
dump 0uaf - /home | (cd /mnt && restore -ruf - )

```
All run perfect and the dump and restore operations complete in due time. Perfect.
But upon completion, I can't work on the partition (like for an fsck for example) because the disk is busy. And stays busy for a very very long time (hours) with the access light on the interface flashing. (did not wait long enough to see the light stopping flashing)
I've a process accessing the disk :
```

lsof | grep sdc1
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/1000/gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.portal file system /run/user/1000/doc
      Output information may be incomplete.
jbd2/sdc1 21618                                root  cwd       DIR              253,2       4096          2 /
jbd2/sdc1 21618                                root  rtd       DIR              253,2       4096          2 /
jbd2/sdc1 21618                                root  txt   unknown                                          /proc/21618/exe

```
So my question is what is going on here and should I worry ? 
And are my backup at risk ? 
Many thanks in advance for your help and answers.
Have a nice and bright day.

---

### Post by MAFoElffen on 2023-10-07
jbd2 is a kernel thread that updates the filesystem journal. 

It can be stopped (in your case) via
```

fuser -km /mnt

```
After that is stopped, that should close that thread. 

If it where me, then I would unmount the drive after that and do fsck on it to ensure everything is okay with it.

---

### Post by georgesgiralt on 2023-10-07
Thank you for your answer.
I did not try that but restarted the computer and then ran fsck. Of course on an unmounted file system. Ran fine, found nothing wrong. 
Then I mounted the disk again. The LED on the SATA/USB interface started again to blink, as soon as the mount was completed. It blinked for a couple of hours and I had a jbd2 process all that time. 
When blinking stopped, the process was gone. 
I don't know what was in the journal of this file system but it took time to process... 
I'll try to do same thing on another disk using the same SATA/USB interface to check if the problem lies in the hardware or in the disk drive itself ? 
I'm accustomed to see the activity LED on old and slow USB stick to blink long after the copy said it is completed, but this behaviour is very strange. Looks like all disk activity was written in the journal instead of the actual disk sector it had to !

---

### Post by MAFoElffen on 2023-10-07
Yes. That is strange.

I would use iostat from the sysstat package if that happens again...
RE: Ubuntu man page iostat--  [https://manpages.ubuntu.com/manpages/xenial/man1/iostat.1.html](https://manpages.ubuntu.com/manpages/xenial/man1/iostat.1.html)
> 
DESCRIPTION
       The iostat command is used for monitoring system input/output device loading by  observing
       the  time  the  devices are active in relation to their average transfer rates. The iostat
       command generates reports that can be  used  to  change  system  configuration  to  better
       balance the input/output load between physical disks.

I would use this command:
```

iostat -tkx 1 1 | grep -v 'loop'

```
Since that command string is not using the -y flag, it will show you all the stats of all the devices since the last boot. The man page (linked above) does a pretty good job explaining what data in the displayed columns mean.

---

### Post by georgesgiralt on 2023-10-08
Thank you, I did not thought about iostat. Not used it since a very very long time. 
Since yesterday, I made a test using another disk. Behaviour is similar (but the blinking last only for some minutes for around 1TB data written to the disk). So it seems the problem lies in the other disk drive. Will redo the backup and see what goes on with iostat. 
Writing 1TB of data on those disks takes time... So I won't do it now, as I've other chores to attend ;-) And a Rugby World Cup games to watch ....

---

