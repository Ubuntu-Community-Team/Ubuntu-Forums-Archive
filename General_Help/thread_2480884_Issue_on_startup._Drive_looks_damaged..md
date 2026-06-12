---
title: "Issue on startup. Drive looks damaged."
date: 2022-11-13
forum: General Help
---

### Post by texpat on 2022-11-13
So this old laptop seems to have problems with its hard drive, if I interpret the screen messages correctly. 

[ATTACH=CONFIG]291248[/ATTACH]

I'd really appreciate if someone could throw some light on what all this means. I don't have physical (or remote) access to the machine so I won't be able to offer much feedback. Really only trying to evaluate how bricked the thing is. There is some data on the disk (photos) that would be nice to recover, but nothing indispensable. Would it be possible to boot off a USB drive and attempt to repair using disk utilities?

Thanks for reading and thanks for any comments or insights.

Tx

---

### Post by MAFoElffen on 2022-11-13
"This old laptop" translates to how old? Make and Model?

Though laptop hardware also means is limited life... I would boot from LiveCD type of media an do an fsck on the partitions of the drive to check it's filesystem health. It may or may not be salvageable... But it is worth a try right?

---

### Post by texpat on 2022-11-16
Marking this as 'solved' to get it out of the way. I just wanted confirmation that the hard drive is the issue, which is pretty much what MAFoElffen confirms - and thanks for that :-)

---

### Post by TheFu on 2022-11-16
For all HDD/SATA issues, I'd run smartctl to see if it is just a cable issue or something worse.

Any drive older than the warrant can fail at any point.  For me, if there are any issue after the warrant is up, I get a replacement ASAP.  My data is more important than a $50 storage device.  Same for backup storage.  Any issue after the warranty is over and it gets replaced immediately.  All my versioned system backups fit onto a 2TB HDD. Those run about $50, so hardly any real hardship to replace, just a minor inconvenience and a few less coffees for the month.

A basic Linux troubleshooting technique is to boot into a "Try XYZ" environment - "Live boot" is another common name.  Those can completely remove storage from the boot issues. Then just install any needed programs into the environment. They will only be there while that boot is powered. A reboot will require re-installing any programs again. After all, the ISO is a read-only medium - which is good for many things.

---

