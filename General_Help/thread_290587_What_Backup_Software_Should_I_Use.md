---
title: "What Backup Software Should I Use?"
date: 2006-11-01
forum: General Help
---

### Post by EmyrB on 2006-11-01
Hi all,

I have a client who has gone for a edgy server install. He has 4 Windows clients and they will be talking to the server through samba. The problem I have is backup software. I know that there are programs called AMANDA and Bacula, but these seem very complicated for what I need.

Is there any backup software out there that will backup data on the server to a tape and that I can schedule to run 5 days a week?

Also, do the above software packages have any gui's or athey purely command line? I know that I can get a webmin module for AMANDA, but even that is very complicated.

Oh and another question, when will ebox ([http://ebox-platform.com](http://ebox-platform.com)) be available for Ubuntu?

Cheers

EmyrB

---

### Post by John.Michael.Kane on 2006-11-01
Have a read.
[http://www.ubuntuforums.org/showthread.php?t=278919&highlight=cron+backup](http://www.ubuntuforums.org/showthread.php?t=278919&highlight=cron+backup)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://www.ubuntuforums.org/showthread.php?t=240326](http://www.ubuntuforums.org/showthread.php?t=240326)
[http://www.ubuntuforums.org/showthread.php?t=80790](http://www.ubuntuforums.org/showthread.php?t=80790)

---

### Post by EmyrB on 2006-11-02
Thanks for that SD-Plissken, but each of the links you posted don't deal with a dat drive. You see the server in question has a dds4 tape drive which they will want to use, so they can take their daily backups out of the office, per their ISO procedures.

---

### Post by John.Michael.Kane on 2006-11-02
Another thought is that you could use a program called **amanda** which should be in the repo's,and it allows for tape backups.

---

### Post by EmyrB on 2006-11-03
Hi SD-Plissken

I have thought about Amanda, but it is very complicated to set up, I was just wondering if there was a Linux version of something along the lines of Backup Exec (now bought by Symantec) as Amanda is as complicated as ArcServe is as it is all done with scripts.

There must be an easy backup solution to this?

---

### Post by Sgurd on 2007-02-09
I'd also be interested in an easy tape backup program.  We use ArcServe on our Windows machines, but I'd imagine it could get tricky in linux for a noob at the command line.

Any new ideas?

---

### Post by pebkac on 2007-02-09
> **Sgurd said:**
> I'd also be interested in an easy tape backup program.  We use ArcServe on our Windows machines, but I'd imagine it could get tricky in linux for a noob at the command line.

Any new ideas?

I personally use Mondo/Mindi for backups, it uses SCSI devices so if the tape drive is SCSI then it might work for you.

I found it quite easy to use, the version I have is command line but they tell you all the commands to type.

You could put those into a cron job to run once a day.

---

### Post by Marsolin on 2007-02-09
I haven't used it myself, but [KDat]("http://linuxappfinder.com/package/kdat") is specifically designed to backup to tape.

---

