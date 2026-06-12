---
title: "GDM could not write to your authorization file"
date: 2007-07-05
forum: General Help
---

### Post by roadkill on 2007-07-05
I got this error when trying to log into Feisty 7.04 this morning:

> GDM could not write to your authorization file.  This could mean you're out of disk space or home directory couldn't be opened for writing.

That makes sense, because the last thing I did before logging out of the previous session was start a backup with only 4.5 Gb remaining.  When I mount my boot partition and use **df -h**, it shows 100% of the space used.

My problem is that even after deleting gigabytes of files, it still shows 100% space used!

I've tried deleting from a Nautilus session started as root and using **rm *** from the console, but neither method makes a difference -- **df -h** still shows that all the available space is in use.

---

### Post by kevinlyfellow on 2007-07-06
That's weird.  Here's a 'stupid' suggestion.  Have you checked all your trash cans?  Make sure to `rm -r home/username/.Trash/*` and for root `rm -r /root/.Trash/*`

Another 'stupid' suggestion, do you have everything on one partition or is your home directory on another partition?  Make sure that your deleting things on the correct partition.

Sorry about giving obvious suggestions, but going on 9 hours, I'm sure you that the worst my reply has done is bumped your post ;-)  BTW, I'm looking around for a good backup utility, what utility do you use to backup?

---

### Post by roadkill on 2007-07-06
> **kevinlyfellow said:**
> Have you checked all your trash cans?  Make sure to `rm -r home/username/.Trash/*` and for root `rm -r /root/.Trash/*`

Thanks for the suggestion, Kevin.  I *hadn't* checked all the trash cans.  I have now though, and it hasn't made a difference to the situation.

What's even weirder is that after I mount the partition (the other one is a Windows partition, so my home directory is in the boot partition) and look at it in the System Monitor, I see this:

```
Device        Directory   Type   Total           Free        Available    Used
/dev/sda2   /mnt          ext3   105.5 GB    3.8 GB    0 bytes      101.7 GB 100%
```

I was using the Ubuntu Simple Backup Config utility and this was my first attempt, so I'm not sure I can make any recommendations.

---

### Post by kevinlyfellow on 2007-07-06
Your not the only one experiencing memory issues.  Another person has an issue with cups mysteriously taking up tons of space.  

[http://ubuntuforums.org/showthread.php?t=493485](http://ubuntuforums.org/showthread.php?t=493485)

Is the problem the same as this persons?

---

### Post by roadkill on 2007-07-06
> **kevinlyfellow said:**
> Your not the only one experiencing memory issues.  Another person has an issue with cups mysteriously taking up tons of space.  

[http://ubuntuforums.org/showthread.php?t=493485](http://ubuntuforums.org/showthread.php?t=493485)

Is the problem the same as this persons?

That may have been it.  I checked the cupsys directory and found no large log files, but while snooping around in /var, I came across the backup I'd made earlier.  **ls -l** showed its size to be 4096 bytes, which obviously wasn't right, based on the headache it had caused me.  I deleted it and restarted, and found that not only was **df -h** now reporting the correct amount of space used, an additional 4 Gb had become available, which is what I'd estimated the backup must have used, in order to suck up all my available space.

Problem solved!

I think from now on I'll back up my important documents by FTP and let the rest hang.

---

### Post by roadkill on 2007-07-06
And once again, thanks for the help.  I would never have fixed it without your advice.

---

### Post by kevinlyfellow on 2007-07-06
No problem, I just happened to have found that previous thread, lucky really.  Quite frankly, I probably would never have been able to figure it out, I'm just a bridge this time around ;-)

---

