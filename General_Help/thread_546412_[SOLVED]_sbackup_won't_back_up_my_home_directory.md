---
title: "[SOLVED] sbackup won't back up *my* home directory"
date: 2007-09-08
forum: General Help
---

### Post by opus1 on 2007-09-08
I configured sbackup using the custom settings and included '/home' as one of the directories to back up.  However, when I look at the files list (or in the *.tgz itself) I notice it doesn't back up *my* home directory.  It will backup the other user's home directory, but not mine.  I even included *my* home directory in the "include" list and it still didn't work.  This is driving me nuts.  

I started sbackup through the command line and recieved no errors.  This is happening with my PC running ubuntu 6.06 and my laptop running kubuntu 6.06.  ](*,)

I've not been real impressed with sbackup due to it's lack of user feedback, but I don't have time to try to figure something else out.  I looked through the forums and there doesn't seem to be another GUI based backup utility out there.

If some one can recommend one, or can tell me why sbackup is misbehaving this way I would really appreciate it.

---

### Post by Goliath! on 2007-09-08
Honestly, I backup using a simple script that tars up what I need saved and copies it to an external disk.  I make it a point to run that script every time I boot up the machine.  It's outlandishly primitive, I know, but it DOES copy my home directory :)

---

### Post by opus1 on 2007-09-09
Thanks for responding Goliath.  What you're doing is the same thing I was before I discovered sbackup.  Then I was lured by the promise of incremental backups!  Too bad it didn't work out.  

I guess I'll go with your suggestion and dig out my old backup script again.  If you want something done right you've got to do it yourself, right? :)

I wish I had some extra time, I'd try to write something myself.  If ubuntu is going to succeed with recent converts from Windoze, they'll need a better GUI backup system than sbackup!

---

### Post by opus1 on 2007-09-30
***UPDATE***

In order to help others with similar problems, here is the solution I used:  After some researching, I found a neat app (which is in the Ubuntu universe repository) called grsync.  It is a graphical front end for rsync.  It allowed me to configure an incremental backup in less than 2 minutes -- and for me right now time is everything.

I followed a good tutorial at [http://mag.mypclinuxos.com/html/Issues/200708/page04.html]("http://mag.mypclinuxos.com/html/Issues/200708/page04.html")

Now, when I find the time, I'll figure out how to do a cron job to run this automatically and it will completely fulfill my requirements.

Cheers.

---

