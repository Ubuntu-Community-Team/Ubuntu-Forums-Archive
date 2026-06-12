---
title: "Cron rsync command question"
date: 2013-03-18
forum: General Help
---

### Post by williammanda on 2013-03-18
I have setup rsync to backup a drive everyday using cron. This is the command:

0 1 * * * /usr/bin/rsync -av --stats --delete /media/sdc1/ /media/sdd1/

My understanding is that the "--delete" will delete any files on the backup drive that are not on the source drive....but it doesn't. The backup drive has accumulated all the files that were deleted on the source drive. If the rync command is correct then why are the files not being deleted or if the rsync command is incorrect please supply the correct command.
Thanks

---

### Post by williammanda on 2013-03-18
The cron was setup as a user not root.
Thanks

---

### Post by williammanda on 2013-03-19
anyone?

---

### Post by papibe on 2013-03-19
Are the source and destination mounted partitions or devices?
What kind of filesystem do they have?

I would recommend using the log options to check for details:
```
rsync  -av  --log-file=/path/to/log/file
```
Regards.

---

### Post by williammanda on 2013-03-19
> **papibe said:**
> Are the source and destination mounted partitions or devices?
Yes they are mounted...I'm not sure I could use them if they weren't mounted. Also they are devices...harddrives...sdc1 and sdd1

> What kind of filesystem do they have?
ext4

> I would recommend using the log options to check for details:
```
rsync  -av  --log-file=/path/to/log/file
```
Regards.
What details am I looking for?

Getting back to my original question....is the "--delete" correctly being used or not?

---

### Post by papibe on 2013-03-19
> **williammanda said:**
> What details am I looking for?
What files are being transfer, what is being deleted, error messages from transfers and deletions.

This could bring to light some permission errors, links, other partitions under it, etc.

> **williammanda said:**
> Getting back to my original question....is the "--delete" correctly being used or not?
Yes. That is the purpose of that option: to make an exact copy of the source.

Regards.

---

