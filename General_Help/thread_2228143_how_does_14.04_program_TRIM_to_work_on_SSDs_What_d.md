---
title: "how does 14.04 program TRIM to work on SSDs? What does the cron look like?"
date: 2014-06-05
forum: General Help
---

### Post by genejohnson55 on 2014-06-05
Does 14.04 put the cron here? [I]/etc/cron.daily/trim
[/I]
I found this on webupd8. Is the 14.04 version by canonical the same or different? 
```
#!/bin/sh
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
fstrim -v /home >> $LOG
```

Is it necessary to fstrim both / and /home if /home is part of the / partition?

---

### Post by QIII on 2014-06-05
To answer your question, yes, you have to trim both partitions.

What brand of SSD do you have?  Last I heard, only Samsung and Intel have TRIM supported by default in Ubuntu.  That may have changed.

---

### Post by oldfred on 2014-06-06
In 14.04 it is this, but in cron.weekly:

```
#!/bin/sh
# call fstrim-all to trim all mounted file systems which support it
set -e

# This only runs on Intel and Samsung SSDs by default, as some SSDs with faulty
# firmware may encounter data loss problems when running fstrim under high I/O
# load (e. g.  https://launchpad.net/bugs/1259829). You can append the
# --no-model-check option here to disable the vendor check and run fstrim on
# all SSD drives.
exec fstrim-all
```

I have not been in my 14.04 enough to know what it is doing. I do not have an Intel nor Samsung SSD, just an inexpensive 2 year old Microcenter house brand model. I changed to the daily task like you posted above.

My log file is growing. My SSD is about two years old and orginally I had discard in fstab, but changed about a year ago.

first entry in log (I do not have separate /home):
*** Sat, 27 Jul 2013 07:44:50 -0500 ***
/: 1856671744 bytes were trimmed

---

### Post by genejohnson55 on 2014-06-06
> **oldfred said:**
> In 14.04 it is this, but in cron.weekly:

```
#!/bin/sh
# call fstrim-all to trim all mounted file systems which support it
set -e

# This only runs on Intel and Samsung SSDs by default, as some SSDs with faulty
# firmware may encounter data loss problems when running fstrim under high I/O
# load (e. g.  https://launchpad.net/bugs/1259829). You can append the
# --no-model-check option here to disable the vendor check and run fstrim on
# all SSD drives.
exec fstrim-all
```

I have not been in my 14.04 enough to know what it is doing. I do not have an Intel nor Samsung SSD, just an inexpensive 2 year old Microcenter house brand model. I changed to the daily task like you posted above.

My log file is growing. My SSD is about two years old and orginally I had discard in fstab, but changed about a year ago.

first entry in log (I do not have separate /home):
*** Sat, 27 Jul 2013 07:44:50 -0500 ***
/: 1856671744 bytes were trimmed

Yeah. I have intel ssd and have been using Discard in fstab. Now that I've decided to stay with 12.04 instead of upgrading to 14.04 (primarily because of my disappointment with Nautilus), I'm looking at switching to fstrim instead.

Unless anyone advises otherwise, I'm assuming it's okay to use the 14.04 trim code in 12.04. I'll copy the shebang script you posted from 14.04 and use it in 12.04.

---

### Post by oldfred on 2014-06-06
I am using the code you posted as I wanted the log file at least initially to know something was happening.
And it seemed daily might make more sense than weekly, but do not know.

---

### Post by genejohnson55 on 2014-06-07
I set mine for weekly after reading your post. I assume canonical based their decision on research. But I could be wrong :)

---

