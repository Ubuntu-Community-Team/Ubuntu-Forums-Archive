---
title: "gnumeric can't open file"
date: 2014-02-14
forum: General Help
---

### Post by mick.cannon on 2014-02-14
I've been using gnumeric every day for a number of years without a hitch. Just tried to open a gnumeric file that was saved yesterday and get the message "XML document is not well formed".  Other saved files do open correctly.  I do back-up the files but only once a week, so I've lost the last few days entries. Can anyone help me recover my lost data.

---

### Post by TheFu on 2014-02-14
How corrupt is the file?  Did you look inside? If it is just XML, perhaps an XML viewer with the DTD would spot issues?

How did the file get corrupted? Could the HDD or SATA cable be failing?

Lastly, perhaps a daily backup would make sense, at least for important files? Some places use hourly snapshots for that stuff. It is unlikely that RAID would have helped. File corruption is likely a program issue.  I know that Back-In-Time supports hourly snapshots and is great for HOME directory uses (not so great for the entire system).

---

### Post by Dennis N on 2014-02-14
If you have Gnumeric version 1.12.6, there is a bug:

[https://bugzilla.gnome.org/show_bug.cgi?id=707047](https://bugzilla.gnome.org/show_bug.cgi?id=707047)

My solution was to revert to version 1.12.1 which can be installed on 13.10:

See post #8 in this thread:
[http://ubuntuforums.org/showthread.php?t=2183427](http://ubuntuforums.org/showthread.php?t=2183427)

---

### Post by mick.cannon on 2014-02-15
Thanks to the two people who tried to help.  I agree i probably should back up more often, though in this case as the saved file was corrupted in some way surely doing a backup would overwrite the last good version and I would have lost even more data.  I had no luck with the two xml viewers I tried, so have now given up and attemted to replace the missing data.  Gnumeric is saving the files properly (as it always has done in the past) so I have no idea what could have caused the problem.

---

### Post by TheFu on 2014-02-15
Versioned backups are critical for just this exact reason.  Back-in-Time (GUI) and rdiff-backup (rsync-like) are highly network and storage efficient with versioned backups.

---

