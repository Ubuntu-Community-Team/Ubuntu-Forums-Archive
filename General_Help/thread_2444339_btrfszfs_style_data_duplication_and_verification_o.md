---
title: "btrfs/zfs style data duplication and verification on DVDR/BDR?"
date: 2020-05-28
forum: General Help
---

### Post by jlparsons on 2020-05-28
Ok possibly a daft question - is there a solution which offers data duplication and verification over one or more optical discs?  Something similar to btrfs raid1 or dup where the system checks for errors using chucksums and replaces any bad blocks with a good copy from elsewhere on the media or from a second identical disc?  Currently I use rar archives for optical backups due to its built in encryption and ability to allocate 10% extra space to data recovery record, but I wondered if there's a better way.  Guessing this would be possible at archive level?

---

### Post by TheFu on 2020-05-29
par2?   If you just want to know whether a file is corrupted, use 1% par2 files. If you want to fix minor corruption, use 5-10% par2 files.  I strongly suspect this is what the rar format uses.

As for data deduplication, there are some backup tool that do that. I've not used them.  Different file types compress better than others.  Trying to compress already compressed files (videos, audio, images, ZIP, and other compressed types) is a mistake and often causes the resulting file to increase in size.  I'd probably just use ZFS compression.

I don't trust btrfs.
[https://wiki.debian.org/Btrfs#Warnings](https://wiki.debian.org/Btrfs#Warnings)
[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/7](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/7).
4_release_notes/chap-red_hat_enterprise_linux-7.4_release_notes-deprecated_funct
ionality_in_rhel7

*<Start RANT:>*
I stopped using optical backups about 10 yrs ago after someone challenged me on the time, cost, effort, over using huge HDDs.  They just aren't cost effective, but mainly due to the time involved.

I'd created a few scripts to optimizing which files were placed onto which optical discs.  gaffitter was the main tool used.

The only reasons to use optical media that I can come up with are:  
[LIST]
[*]Very long-term storage - say 200 yrs, but the media and writers are EXPENSIVE. Specific storage environment requirements must be included
[*]Video or audio media to be played back on specific optical-only devices
[/LIST]

That's it.

Back in the early 1990s, I had a task to migrate a bunch of data for the facility from nearly dead tape formats onto newer formats.  We're talking 1/4 inch tapes and moving to 4mm back then. Hundreds of 1/4inch tapes would fit onto a single 4mm.  That taught me an important lesson.  All data formats die.  We always need to move forward any data to which we want to retain access.  Just last week, I discovered that my only remaining 3.5inch floppy disk drive isn't working. It won't read any floppy disks anymore and my newer systems don't even have the correct type of connector on the motherboard.  I retained a 5.25inch floppy disk AND (CPU+RAM+MB+GPU) just so I'd be able to access that data.  I probably have hundreds of both types of floppies.  Think I may have made copies onto some QIC-250 tapes years ago.  Still have that tape drive somewhere, but don't know if any of my current machines have parallel ports anymore.  Effectively, I've totally screwed up and didn't move the old data soon enough to some USB device.  Deduplication or not.

---

