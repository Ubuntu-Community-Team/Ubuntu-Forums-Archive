---
title: "Recovering NTFS files from ext3 partition..."
date: 2007-01-09
forum: General Help
---

### Post by blackcoatman on 2007-01-09
I had Windows XP pro x64 installed on one partition and kubuntu on the other. I decided to reinstall Ubuntu, so I boot from the live cd. I don't remember seeing any choice for the partitions, so maybe this was the dumpest thing ever happened and maybe I just clicked next without noticing... I have no idea how this happened. So here I am with a clean Linux-only computer (it was a shock to see that Grub didn't show up as a menu and automatically booted Ubuntu... - and rather faster than with Windows on the hard disk...). Now at least I wish to see if I can recover any files that I might need from the deleted ones... Is there a way to do this? I run TestDisk but it doesn't show me my HD partitions, just the cdrom! Any ideas, programs etc?

---

### Post by dcstar on 2007-01-09
> **blackcoatman said:**
> I had Windows XP pro x64 installed on one partition and kubuntu on the other. I decided to reinstall Ubuntu, so I boot from the live cd. I don't remember seeing any choice for the partitions, so maybe this was the dumpest thing ever happened and maybe I just clicked next without noticing... I have no idea how this happened. So here I am with a clean Linux-only computer (it was a shock to see that Grub didn't show up as a menu and automatically booted Ubuntu... - and rather faster than with Windows on the hard disk...). Now at least I wish to see if I can recover any files that I might need from the deleted ones... Is there a way to do this? I run TestDisk but it doesn't show me my HD partitions, just the cdrom! Any ideas, programs etc?

If you have only a single Linux partition now then you may well have wiped your previous Windows partition - install the **gparted** package to verify this.

If there is only one partition listed, then there is little (if not zero) hope of recovering your Windows data.  :(

---

### Post by az on 2007-01-09
Foremost can recover files.  Even if you formatted your partition as ext3, some of the data is still be there.  You need a seperate disk to write them to.  Also, stop using that partition - use the live cd so that you don't overwrite any data you could want to recover.

In Edy, install foremost from the universe repository.  In Dapper, get it upstream and compile it - the verison in Dapper is a little old. ([http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)) You can do this from the live cd.

Mount the drive where you want to dump all your rescued files and then run



sudo foremost -i /dev/hda1 -o /media/usbdisk/

where hda1 is your only partition on the disk (other than swap) and your usbdisk is mounted in /media/usbdisk/...


Good luck.

Not everything is lost, but lots is.

---

### Post by Rhubarb on 2007-01-09
Your new (K)ubuntu install sounds very much like you've wiped the hard disk clean and hence would've installed directly over the space on the hard disk where windows used to reside.
If you're lucky and (K)ubuntu installed itself tightly packed up at the start of your hard disk, then there's a chance your windows documents may still be recoverable.
 
If you really want those documents recovered, then take your hard drive to a data recovery specialist.
If you just want to try yourself to recover that data (and risk losing your documents so a data recovery specialist is unable to perform), then IMO I'd put your windows CD in the drive, let it partition the drive as NTFS (quick format), then if you've got a spare drive (or not), install windows and a NTFS file recovery program - tell it to scan the whole hard disk.
You might be lucky there.

It's a lot of effort to do all this, but in future please please please consider backing your documents up on a regular basis.

Edit: I'd try azz's method first, it should me a bit more safer than my method.
But of course if you have the money, take it to a data recovery specialist - it's what they do (and do very well).

---

