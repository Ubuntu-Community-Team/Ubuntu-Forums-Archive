---
title: "CDROM shell game"
date: 2006-11-24
forum: General Help
---

### Post by XPuntu on 2006-11-24
Hi All,

First a description of what I have. I have a CDROM drive and a DVDROM drive.

If I insert a DVD in the DVD drive, an icon pops up on my desktop and totem starts up. Nautius shows a CD-RW drive and CD-RW/DVD+-R Drive icon. (which has a round cd icon) \\:D/ 

If I insert an audio CD in the DVD drive, sound juicer pops up with the disc info but no icon on my desktop. And no change to the basic icon in nautilus. If I double click on the CD-RW/DVD+-R Drive icon I get the following message 

"Unable to mount the selected volume. The volume is probably in a format that cannot be mounted"

When I click on more details I have this: 
"mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
missing codepage or other error
in some cases useful info is found in syslog - try
dmesg | tail  or so"

BUT I can still play the CD in sound juicer! :-k 

If I insert the CD in my CD drive, no sound juicer, no icon and nothing in nautilus. Double clicking the CD-RW drive icon gives me this message: "mount: mount point /media/cdrom1 does not exist"

But, I have been able to burn data and audio CDs with the CD drive using Gnomebaker!

I've tried to mount the drives in fstab like so

/dev/hdc        /media/cdrom	udf,iso9660 user,noauto	0	0
/dev/hdd	/media/cdrom1	udf,iso9660 user,noauto	0	0


If I type "sudo mount /media/cdrom/ -o unhide" I get the following

mount: /dev/hdc already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/hdc is already mounted on /media/cdrom0

Not sure why it says cdrom0 though

I looked at the UDFS but the commands don't seem to help with trouble shooting.

Any suggestions? Is there a step-by-step I can work through?

Thanks for your suggestions.

---

### Post by po0f on 2006-11-24
XPuntu,

You can't mount audio CDs.  I don't know all the technical mumbo-jumbo, just the fact.

---

### Post by XPuntu on 2006-11-24
Thanks Po0f. I&#314;l take your word for it. 

So I load a data CD into the CDROM drive. No icon shows up on the desktop. I look in Nautilus and a third (!) volume shows up called "CD-RW/DVD+-R Drive (2)" is there. When I double click that, I get the following message:

"Unable to mount the selected volume" the details tell me "mount:no medium found" 

When I load the CD into the DVD drive, I get the icon on my desktop but nautilus still shows three CD/DVD drives and double clicking the CD/DVD(2) actually works. This is too weird. Maybe I've named the drives incorrectly? I'm going to try taking them out of fstab and see what happens.

---

### Post by XPuntu on 2006-11-24
Well everything works now. I #d the lines (rem'd ?) relating to the optical drives and now they're acting normal, automatically mounting when I pop in a cd or dvd.

Seems odd that I don't have to put them in fstab. I guess I'm not using it properly.

---

