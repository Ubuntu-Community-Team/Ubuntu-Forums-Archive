---
title: "Making new space for backups"
date: 2014-12-05
forum: General Help
---

### Post by Richard_York on 2014-12-05
I'm running Ubuntu 14.04 LTS, on 32 bit. I have two matching 155GB hard disks in the machine, one to act as a backup. It's been happily running weekly backups onto this second disk, ever since Ubuntu installation.
 Yesterday's failed due to lack of space. I realised that the "keep" setting was on "for ever". (Now changed that to "6 months", but that won't have affected anything yet.)
I made a complete new backup to an external drive, then moved most of the contents ( I also keep some other data stored there) of the internal backup disk to the rubbish bin, which I've emptied. 
I assumed I could now start backups again on the internal drive, but it's again failed due to lack of space.
"Properties" shows it to be fully used, despite my moves to empty it.

How can I really empty this space, please?

Replies in non-geek language will be gratefully welcomed :-)
Thanks.

---

### Post by TheFu on 2014-12-05
First, it would help if you shared what backup tool/method is being used?
I use rdiff-backup and have been mostly happy with it for about 4 yrs. Prior to that, I used hardlink-based rsync tools.  A mirror is fine for baby-backups, but for real powerful and more secure backups, versioned backups with 30-120 days of differentials is mandatory. There are so many reasons why a mirror is just not enough of a back to explain.

[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) is the best how-to for rdiff-backup that I've seen. Better than my feeble attempts to share how I do it.

---

### Post by Richard_York on 2014-12-05
Thanks very much for this.
 I'm simply using the backups tool which comes built in to 14.04, via the "System Settings" menu. In my ignorance I've no idea what it's called. It's been set to run once a week. 
I do realise it's not a regular mirror system - the second disk was installed when the computer was on Windows, with the idea of using it as a mirror. Since conversion to Ubuntu it's just a handy place to send the backups so I don't clog up my working hard drive. This may not be good practice, it just seemed a good way of using the space available.
I'll read the link with interest, thanks for this. Initially I assume there's a better way of making the existing system work, unless in my ignorance there's something I'm missing here.

---

### Post by TheFu on 2014-12-05
I'm completely ignorant about the Ubuntu GUI - don't use it myself.

I'm concerned based on some of the wording above - calling a disk/partition a "backup" and placing primary data there means is isn't a backup disk/partition anymore. It is primary.  If there is any data on that disk that isn't somewhere else too, it isn't a backup anymore. Hope that is clear.

Funny story - I gave Mom a USB drive in the late 90s and told her to copy important files there as a 'backup' - later I learned that she'd been copying files there from the main disk and deleting them from the main disk since they were "backed up now". ;)  1 copy is NOT a backup.  In the end, Mom never understood and I took over all backup stuff for her Lubuntu machine from 3 states away.  I setup local and remote backups for her and didn't allow her any access to the backup storage. That prevented the confusion going forward.  

Daily data backups is very important to any system on a network, IMHO. But it is just about the risk profile - how likely either a HW failure, data corruption or being hacked is on any single day. If the system runs a web browser or email client, I think daily backups are the minimum required for any system with internet access. Call me paranoid.

---

### Post by Richard_York on 2014-12-05
I like the story of your Mom! I accept that it's not ideal having the two disks on the same machine, but I hope it counts as a backup - each week it copies the contents of the "Home" directory on the working hard drive to this second disk in a form where by pressing the "restore " button it should restore the system in the event of that drive failing, crashing, etc. Every so often, not so often as I should, I do an extra backup to an external hard drive, in case of machine failure.
I quite accept I should do this daily...

Meanwhile I can't yet find the answer to my original query of how to persuade the machine that having moved all that old data to the Rubbish bin, and emptied it from there, there should now be space available on this second disk, and there isn't.

Thanks for your help so far, again.

---

### Post by TheFu on 2014-12-05
Is there a "Help--> About" in the backup tool you are using?  It really is needed to know which backup tool is being used. These have changed over the years, so the default tool may not be what is expected.  Is it dejadup?  Have you been cleaning up old backup sets?

---

### Post by p-bethe on 2014-12-05
I am kind of new myself, so I thought I could learn something here.  The name of the tool is Backups.  I called it up, but I can't figure out how to call up Help.  There must be some way that everyone should know, but I don't.  We thank you for you patience.

---

### Post by p-bethe on 2014-12-05
OK, I answered my question.  F1 brings up help for Backups.  This program is called 
[h=2]*Déjà Dup.*[/h]

---

### Post by Richard_York on 2014-12-05
p-bethe, you answered it for me too - it didn't occur to me to use F1: I said I needed non-geek language and this shows just how deep this goes ...  indeed, it's called Deja Dup. Thanks :-)

---

### Post by TheFu on 2014-12-05
Since I don't use that tool, perhaps [http://askubuntu.com/tags/deja-dup/hot](http://askubuntu.com/tags/deja-dup/hot) will be of help?
Look for the delete old backups part or making room for new backup part.

---

### Post by Richard_York on 2014-12-05
I will look more into this link - time doesn't allow until later this w/e now! Meanwhile there's an answer to a similar query to mine there which seems to indicate there's a possible bug. If that doesn't work, maybe I should be looking at a different tool, even the one you mentioned earlier?
Thanks again. 
Now to prepare Tudor Christmas music for an event tomorrow!!

---

