---
title: "cp command sometime fails to save time fractions"
date: 2018-09-10
forum: General Help
---

### Post by Skaperen on 2018-09-10
in a typical day i probably copy files with cp or run scripts (bash and python) that invoke cp (via subprocess.call in python) to copy files nearly or well over 1000 times. many times as root though usually more often a non-root user.  the -p option is consistently used though not always.

what i am seeing is that the modification time of the files, whether retained from the original (most instances) or not, frequently has all zeros for the fraction of a second part and sometimes with just microsecond resolution.  but also often it gets the full nanosecond resolution.  these 3 varieties of time settings happen whether the time value is copied from the source file (the -p option) or not (time should be when copying happens).  the full nanosecond setting happens about 80% of the time and the other two cases (microsecond or whole second) about 10% of the time each.

other programs that write data and get a new current time setting also see this happening, but it is about half as often to get microsecond and whole second.

this never happens to rsync.  it always gets the full nanosecond modification time setting.

about half of the file space is ext4 and the rest is encfs on top of ext4.  the issue happens on both.  i am running 16.04 LTS upgraded about every week or two.

anyone have any idea what is going on?  it's not causing any breakage as far as i can see.

---

