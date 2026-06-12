---
title: "Root's crontab being deleted on 12.04"
date: 2013-03-22
forum: General Help
---

### Post by fmmarzoa on 2013-03-22
Hi there,

It seems like my root's crontab file were being deleted. :-?

I edited it yesterday as:

sudo crontab -e

And add a line.

This morning I noticed the command wasn't executed at all, so I open it again:

sudo crontab -e

For my surprise, the command was removed :-? there were only the heading comments of the void crontab as it comes on a new install.

I thought I could did something wrong, so I try it again. This time I first do:

sudo su

To be sure I was root. And then:

crontab -e

I add my line to the crontab file and save it. To be sure about that, I executed again:

crontab -e

And I found that the line I was added was actually there.

Well, a couple of hours later I noticed that the command weren't executed neither, so I run again:

crontab -e

And my command was NOT there.

So it is pretty clear that something is removing it. Now the question is WHAT?

Any ideas?

Bests,

---

### Post by fmmarzoa on 2013-03-26
Hi,

I am the only one who has experienced this problem? Should I fill a bug report or so?

Bests,

---

### Post by SeijiSensei on 2013-03-26
Well it's pretty unlikely the line is being removed.  The most likely guess is that it isn't being saved even though you think it is.  A much less likely possibility is that somehow the system reverted to the prior version of the file.

When you say you verified that the line was still there, did you examine /var/spool/cron/root directly after editing it?  After you save the file use "sudo more /var/spool/cron/root" to verify that the file was actually changed.

---

### Post by fmmarzoa on 2013-03-29
Hi SeijiSensei.

Yet, the line was there, and so the /var/spool/cron/root file *but* I have realized now that /var/spool is mounted on a ramdisk, as part of the optimizations I introduced when I moved from my former HDD to the SSD following these advices:

[http://apcmag.com/how-to-maximise-ssd-performance-with-linux.htm](http://apcmag.com/how-to-maximise-ssd-performance-with-linux.htm)

And so, everytime I shutdown my desktop computer all the crontabs in the spool are lost.

Elementary... X-)

The solution is pretty easy now that I have discovered the cause.

Bests,

---

### Post by SeijiSensei on 2013-03-29
I hope you're not running a mail server!  You'd lose all your mailboxes and the mail queues if they are on volatile storage.

---

### Post by draki on 2013-05-05
I had the same problem - and the same cause..

thanks for posting this - it was driving me mad!

---

