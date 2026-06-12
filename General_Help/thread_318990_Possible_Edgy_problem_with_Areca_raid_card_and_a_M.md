---
title: "Possible Edgy problem with Areca raid card and a MythTV question"
date: 2006-12-14
forum: General Help
---

### Post by admiralawesome on 2006-12-14
The board ate my first post.  Hopefully I can remember everything from my first attempt:

I have a machine with an Althon 64, on a Jetway 939GT4-SLI-G motherboard, with 1GB of ram, an S3 video card, and an Areca 1230 raid card.  The machine passes memtest, burn in tests, etc.  It's made up of all known-good and tested components (as far as working, not necessarily linux-compatible stuff).  I'd like for this to be a file server/MythTV backend.  I'd been trying to use Ubuntu Edgy, because it has packages for MythTV .20 in the repos.

I think I may have run into a problem with Edgy.  The system often freezes when I'm transferring data from an external hard drive (connected via USB) to a 900GB volume on the raid card (four 300GB drives in RAID5, all done in hardware).  The freezes only occur while data is being transferred, and not while the machine is sitting idly.  For the OS drive, I've tried a few IDE drives and a SATA drive (attached to the board's ports, not the Areca card).  I've tried formatting the 900GB volume as ext3 and XFS; the freezes occur with both. The external drives I'm transferring data from are formatted as NTFS, FAT32, or ext3; the freezes occur with all of them.  I only tried Ubuntu Edgy, not any of the other Edgy flavors, so I couldn't say if the problem is specific to Ubuntu or not.  There weren't any errors in any of the logs I looked at to indicate anything was wrong.  I ended up ditching Edgy and going with Kubuntu Dapper, and behold, it works perfectly.  Maybe something is different in Edgy from Dapper regarding Areca support?

I don't have time to bring this machine down to do any more testing with Edgy, but I can give more specs if anyone wants.  Is that enough information to file a bug report?  What I'd really like to know is can I use the MythTV .20 packages from Edgy with Kubuntu Dapper?  I've done a couple of installs of .19 on Dapper, but I'd much rather have .20.  If using the packages from Edgy is any easier, I'd like to use them.  Any foreseeable problems with using the Edgy packages, or know of any guides for MythTV .20 on Dapper?

---

### Post by superm1 on 2006-12-15
> **admiralawesome said:**
> The board ate my first post.  Hopefully I can remember everything from my first attempt:

I have a machine with an Althon 64, on a Jetway 939GT4-SLI-G motherboard, with 1GB of ram, an S3 video card, and an Areca 1230 raid card.  The machine passes memtest, burn in tests, etc.  It's made up of all known-good and tested components (as far as working, not necessarily linux-compatible stuff).  I'd like for this to be a file server/MythTV backend.  I'd been trying to use Ubuntu Edgy, because it has packages for MythTV .20 in the repos.

I think I may have run into a problem with Edgy.  The system often freezes when I'm transferring data from an external hard drive (connected via USB) to a 900GB volume on the raid card (four 300GB drives in RAID5, all done in hardware).  The freezes only occur while data is being transferred, and not while the machine is sitting idly.  For the OS drive, I've tried a few IDE drives and a SATA drive (attached to the board's ports, not the Areca card).  I've tried formatting the 900GB volume as ext3 and XFS; the freezes occur with both. The external drives I'm transferring data from are formatted as NTFS, FAT32, or ext3; the freezes occur with all of them.  I only tried Ubuntu Edgy, not any of the other Edgy flavors, so I couldn't say if the problem is specific to Ubuntu or not.  There weren't any errors in any of the logs I looked at to indicate anything was wrong.  I ended up ditching Edgy and going with Kubuntu Dapper, and behold, it works perfectly.  Maybe something is different in Edgy from Dapper regarding Areca support?

I don't have time to bring this machine down to do any more testing with Edgy, but I can give more specs if anyone wants.  Is that enough information to file a bug report?  What I'd really like to know is can I use the MythTV .20 packages from Edgy with Kubuntu Dapper?  I've done a couple of installs of .19 on Dapper, but I'd much rather have .20.  If using the packages from Edgy is any easier, I'd like to use them.  Any foreseeable problems with using the Edgy packages, or know of any guides for MythTV .20 on Dapper?

Well I can add in my 2 cents.  I've never had good luck with transfers to external usb drives that are large and sustained.  I've experienced similar lock ups and account it mostly to shoddy chipsets and poor connectors on the external drives.  I've tried 3 different usb->ide bridges, on 3 seperate boxes (windows on a roomates's machine, gentoo, and dapper), with the same results.

As for your question about using the 0.20 packages on Kubuntu, you won't have any trouble using 0.20 packages on dapper, but you'll need to use the repository that is built for dapper that I'm running.  It's basically the released edgy version just built for dapper.

deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main

If you are looking for information about myth 0.20 though, troubleshooting, plugin info and the like for ubuntu - see the community wiki page
[http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)

The dapper pages aren't done (and probably won't be for some time at least by me), but the edgy pages are very valuable information.

---

### Post by majoridiot on 2006-12-15
the .20 mythtv packages and set-up info mario provides are the most painless set-up
for mythtv you will find, IMO.

i reverted back to dapper when i had a plethora of sketchy edgy problems and used mario's
guide/packages on a fresh .20 install with no problems whatsoever.

---

### Post by admiralawesome on 2006-12-15
Awesome.  Thanks for the links, I'll give that repo a try today.

---

