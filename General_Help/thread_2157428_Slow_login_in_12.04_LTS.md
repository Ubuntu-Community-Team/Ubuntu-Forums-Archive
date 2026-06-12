---
title: "Slow login in 12.04 LTS"
date: 2013-06-25
forum: General Help
---

### Post by cecilieaux on 2013-06-25
When I enter my login password and press Enter, or click, it takes entire minutes before Unity appears and the desktop is available for use. This began after some time of usage (months, I suppose). I don't have a precise moment I noticed it.

I am running a Dell Precision 390 (Intel® Core™2 CPU 6700 @ 2.66GHz × 2, with 3.9 GB RAM) and Ubuntu reports the graphics card as Gallium 0.4 on ATI RV530. It's a fast machine in Windows XP and WAS even faster in Ubuntu until this started.

I pruned my startup programs to: Autokey, Classic Menu Indicator, Dropbox, Weather Indicator. I have used these for a long time and my system logged in just fine after I installed them.

I'm thinking it may be Unity, because when I try without Unity it seems marginally faster. Although today, both Classic Gnome and Unity logins were as slow as molasses.

I'd appreciate suggestions for fixing this. I'm thinking of abandoning Ubuntu for Mint.

---

### Post by TheFu on 2013-06-25
When things get slower, I always start by checking the system log files for warnings and errors.  A loose SATA cable that isn't completely off can cause this, as can partially failing HDDs. Check the logs.

I would also check your networking. Don't these new-fangled "social apps" all startup automatically and try to check all those accounts? Disable them all. Again, the log files should show if there are issues.

Also, when you first noticed it, if you'd have restored from the backup the day prior, you'd know if it were a software issue.  Backups are always a good idea, but whenever something isn't working perfectly (that used to work great), then is especially the time to get your versioned backups working.  "Versioned" is critical, as a 100% mirror that you can only keep 1 copy of doesn't help if you need to restore files or an entire set from 31 days ago.

Checking the log files should tell you where the issue are: [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)  I'm sure there's a GUI way in Ubuntu, but since I have never used Unity more than a week, I can't say how to get there.

---

### Post by kclark on 2013-06-25
> **TheFu said:**
> When things get slower, I always start by checking the system log files for warnings and errors.  A loose SATA cable that isn't completely off can cause this, as can partially failing HDDs. Check the logs.

I would also check your networking. Don't these new-fangled "social apps" all startup automatically and try to check all those accounts? Disable them all. Again, the log files should show if there are issues.

Also, when you first noticed it, if you'd have restored from the backup the day prior, you'd know if it were a software issue.  Backups are always a good idea, but whenever something isn't working perfectly (that used to work great), then is especially the time to get your versioned backups working.  "Versioned" is critical, as a 100% mirror that you can only keep 1 copy of doesn't help if you need to restore files or an entire set from 31 days ago.

Checking the log files should tell you where the issue are: [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)  I'm sure there's a GUI way in Ubuntu, but since I have never used Unity more than a week, I can't say how to get there.

+1 on the loose SATA cable, I had a similar problem with an encrypted LVM.  I have a 128GB SSD for my system and /home is stored on a 1TB traditional HDD, I started to have slow logins, I'm talking 5-10 minutes with an AMD 6 core, 16GB of RAM, and the SSD + the 1TB HDD.  I couldn't figure it out then I reseated the SATA cable and it solved my problem.  It took me forever to figure out because I thought a loose cable seemed silly, but I guess I was wrong.

---

### Post by cecilieaux on 2013-09-08
This was NOT helpful.

---

