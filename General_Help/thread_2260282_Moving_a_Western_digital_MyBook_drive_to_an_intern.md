---
title: "Moving a Western digital MyBook drive to an internal drive?"
date: 2015-01-10
forum: General Help
---

### Post by mrule on 2015-01-10
I'm trying to move a 3TB EXT4 formatted drive from a WesternDigital USB enclosure to become an internal SATA drive.

The drive contains data so reformatting is to be avoided -- although I can take the data off the drive first.
Once inside the machine, the drive is showing up as unformatd, 2.2TB, with no recognizable label. Anyone know what's going on? This seems very strange.

This post at first seemed relevant, but in this case the user was able to view partitions via parted that I cannot
[http://john-hunt.com/2013/04/25/recovering-data-from-a-wd-mybook-live-2tb-3tbor-similar/](http://john-hunt.com/2013/04/25/recovering-data-from-a-wd-mybook-live-2tb-3tbor-similar/)
I just see "Error: /dev/sdc: unrecognised disk label" when I try that.

Any clue what's happening here?

Update: I tried placing the drives on a different machine. In that machine the partitions show up as 3TB but still are unreadable.

---

### Post by Mark Phelps on 2015-01-10
WD external drives often come with default WINDOWS software that allows you to password-protect the drive.  Trouble is, that after that, only WINDOWS can read the drive.

Did you first access this drive using Windows? Or, have you always accessed this drive using Linux?

---

### Post by pqwoerituytrueiwoq on 2015-01-10
even so can you still use dd to clone it from usb to internal?

you could just take it out of the usb case and put it inside the computer and connect it like any other OEM HDD

---

### Post by mrule on 2015-01-10
Hi! Thank's for your reply! The drives are formatted ext4 and can be mounted / accessed via linux from their USB enclosures, but not when I hook them up to the internal SATA bus.

---

### Post by mrule on 2015-01-10
"you could just take it out of the usb case and put it inside the computer and connect it like any other OEM HDD "

That is exactly what I have done. The problem is that the drive looks completely different when I do this! Somehow the HDD that is exposed through the USB interface on the MyBook enclosure is different from the HDD that is actually within the enclosure. When I move the drive to the internal SATA bus, I can no longer read it, it shows up as an unlebeled and unformatted 2.2TB drive, when in reality it is an EXT4 formatted 3TB drive.

---

### Post by mrule on 2015-01-14
It seems like this might be an unsolved problem with how WD formats the drives inside MyBook. 

This post: [http://lists.centos.org/pipermail/centos/2013-March/133019.html](http://lists.centos.org/pipermail/centos/2013-March/133019.html) reveals a possibly similar situation,  which was never really resolved. It seems like some people are able to **reformat** these drives to work in linux, but no one has been able to mount a previously formatted drive to view or recover the data from a MyBook drive enclose.

---

### Post by mrule on 2015-01-14
I'm continuing to do research. This output might help:

$ dmesg | grep "[sh]db"
[    1.879912] sd 7:0:0:0: [sdb] 5860533168 512-byte logical blocks: (3.00 TB/2.72 TiB)
[    1.880995] sd 7:0:0:0: [sdb] 4096-byte physical blocks
[    1.881460] sd 7:0:0:0: [sdb] Write Protect is off
[    1.881523] sd 7:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.881686] sd 7:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.304132]  sdb: unknown partition table
[    2.304893] sd 7:0:0:0: [sdb] Attached SCSI disk

---

### Post by Holger_Gehrke on 2015-01-14
Seems like WD uses some unusual partitioning scheme. MBR is only defined up to 2TB for Disks with a block/sector size of 512 Bytes and GPT would be recognized. So the Logic in the enclosure obviously does more than just expose a sata disk through USB. Your best bet seems to be to put it back in the enclosure, move the data off, pull it out of the enclosure again and put it into your PC, repartition, reformat and finally put the data back.

---

### Post by mrule on 2015-01-15
Yes, I'm afraid you might be right Holger. Copying the data is feasible though, so I'll do that. Based on the rumours I've found on the internet, these drives are GPT with 4096 sized blocks. It's a shame linux doesn't have any tools to mount and recover data from WD drives -- it is important for recovering data when the enclosures fail. In fact, I'm a little surprised WD hadn't taken an effort to make supporting their drives easier -- making data recovery possible in the event of an enclosure failure would seem like a relatively high priority.

---

### Post by DuckHook on 2015-01-15
> **mrule said:**
> ...making data recovery possible in the event of an enclosure failure would seem like a relatively high priority....except that their customer base are non-geeks who wouldn't know what to do with a bare drive if their lives depended on it. In event of a failed drive, those within warranty would simply ask WD to recover their data. Those out of warranty would either pay WD to do so, or count it up as a lesson learned.

To be fair, WD does state in all of their literature in boldfaced type that HDDs have limited lifespans, that all drives eventually fail, and that users really need to back up their data. My drive even came with backup software, albeit only for Windows. In my experience, about one in five users pay heed to these warnings and regularly back up their data.

It is wiser to treat these drives as a cheap and convenient NAS rather than anything reliable. ssh into it and set up a cron job that rsyncs it to another NAS once a week (for redundancy). Once a month, rsync to a second NAS in true backup mode. Twice a year, take a further backup and remove it to offsite storage. I realize that I've just cast myself as part of the tinfoil hat brigade, but it is unlikely that I will ever have to deal with the misery of recovering crucial data files when my drive dies or even if my house burns down.

I will say this: despite putting in a proprietary (or at least, an obscure) partitioning scheme, Western Digital has made it relatively easy to ssh into their boxes and set up all of the cron jobs, mountings and rsyncs needed to do proper redundancies and backups. Not all NAS vendors are so accommodating.

---

### Post by mrule on 2015-01-18
Ah, yes, I just meant that it would be nice if WD documented / published the partition scheme for the MyBooks so that linux users-developers could figure out how to pull the data off. Design constraints probably limit what they can change on the actual hardware end.

---

### Post by DuckHook on 2015-01-18
I agree with you. How I hanker for the old days when a sufficiently motivated hacker could open up the guts of a black box and figure out what was inside because it was all out laid out in front of him and wasn't "protected" by layer after layer of encryption, DRM-crippleware, intentional obscurity and proprietary BS. My first NAS was an HP Media Vault mv2010. Not only was it a marvel of tight OS design (it runs on a total of 64KB of RAM&#8213;that's K as in Kilobytes!), but there were actually hacker guides put online by members of the original development team that showed you how to enhance its features even further.

I wouldn't hold my breath trying to find for documentation from WD. However, I did find [this]("http://john-hunt.com/2013/04/25/recovering-data-from-a-wd-mybook-live-2tb-3tbor-similar/") tutorial in a Google search from someone who's obviously done something of the sort. You are on your own using those instructions. I've never had to recover a WD NAS and am just acting as an info middleman here.

For what it's worth, my WD NAS is in fact a MyBook Live, so these instructions could prove very valuable for me should my enclosure fail but HDD remain intact. You don't mention if yours is a NAS or just a USB drive. Hopefully, both drives share a common internal architecture and these instructions work for you. Let us know how it goes.

P.S. Even if you succeed in mounting the drive, I would suggest as a previous poster&#8213;move the data off drive, reformat it into a conventional one, and move the data back on. You probably don't want an oddball component as a regular part of your production box.

---

### Post by DuckHook on 2015-01-18
Upon further reading, and going back over your intial post, it seems that you are trying to recover a USB drive. Mounting this drive on a SATA port *will not work*. I should have remembered that once data is funnelled through a USB port, it goes through a firmware translation that renders the files and partition structure quite different from the one expected in a SATA HDD. So, it is doubtful that the instructions in my previous link will work and you might end up corrupting your drive.

Instead of trying to fit a square peg in a round hole, I would strongly recommend just backing up the data with HDD in the USB enclosure, then reformatting the HDD as pure SATA, then putting the data back on. Anything else is just playing with fire.

---

