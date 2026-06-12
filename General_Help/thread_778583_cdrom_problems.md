---
title: "cdrom problems"
date: 2008-05-02
forum: General Help
---

### Post by ainsworth on 2008-05-02
Hi,

A few days ago my cdrom messed up and stopped working (around the time I updated to Hardy). Since then I have a blank disc icon on my desktop permanently that I can't get rid of. Also the drive won't open, nor read anything while in Ubuntu. It seems to work fine before it fully boots (opens and reads discs) but then stops when booted. I just reinstalled Hardy with no problems but the cdrom is behaving the same! The eject command gives the following output:

andrew@andrew:~$ eject -v cdrom
eject: device name is `cdrom'
eject: expanded name is `/dev/cdrom'
eject: `/dev/cdrom' is a link to `/dev/hda'
eject: `/dev/hda' is not mounted
eject: `/dev/hda' is not a mount point
eject: `/dev/hda' is a multipartition device
eject: trying to eject `/dev/hda' using CD-ROM eject command
eject: CD-ROM eject command succeeded

andrew@andrew:~$ eject -v cdrom0
eject: device name is `cdrom0'
eject: expanded name is `/media/cdrom0'
eject: `/media/cdrom0' is not mounted
eject: `/dev/scd0' can be mounted at `/media/cdrom0'
eject: `/dev/scd0' is not a multipartition device
eject: trying to eject `/dev/scd0' using CD-ROM eject command
eject: CD-ROM eject command failed
eject: trying to eject `/dev/scd0' using SCSI commands
eject: SCSI eject succeeded

On cdrom, nothing happens, my other drive (cdrom0) works perfectly and ejects as it should. Any ideas?

---

### Post by aldodefilippi on 2008-05-02
I've got the exact same problem with Ubuntu 7.10 after I downloaded VirtualBox. 
My OS is Ubunty 7.10. I downloaded VirtualBox and since then my CD is not recognized anymore. 

This is the message I get get when I try to open/access my CD drive:

"desktop configuration file unknown"

When I click that, I get this response:

"Unable to mount the selected volume"

When I ask for details I get:

"special device /dev/scdO does not exist"

Can anyone help me out here? As a desperate measure I was thinking of reloading with Ubuntu 8.04 and reformatting but I'll lose some photos which I did not have a chance to back up to a dvd. The same thing occurs to me when I insert a cd/dvd before it boots completely. Thanks a million. regards

When I enter "eject" command in the terminal I get this:

aldo@aldo-desktop:~$ eject -v cdrom
eject: device name is `cdrom'
eject: expanded name is `/media/cdrom'
eject: `/media/cdrom' is a link to `/media/cdrom0'
eject: `/media/cdrom0' is not mounted
eject: `/dev/scd0' can be mounted at `/media/cdrom0'
eject: tried to use `/dev/scd0' as device name but it is no block device
eject: unable to find or open device for: `cdrom'
aldo@aldo-desktop:~$

---

### Post by ainsworth on 2008-05-04
bump

---

### Post by jkman on 2008-05-18
I'm having the same issue.  A reboot fixes the issue...kind of.  If I reboot, the system recognizes the cd, but if I try to eject the drive it stops responding and the icon for the drive changes to the default icon for optical drives.  It worked fine with 7.10, but ever since installing Hardy I've had this issue.

---

### Post by student eternal on 2008-05-20
Hrmm, any one having any luck on this? I have a similar issue, i upgraded to hardy and my CDrom drive vanished completely.  I tried to remont the drive, but any device names I could think of return an error: "Can't find cdrom in /etc/fstab or etc/mtab"

I am still pretty new to Linux and Ubuntu in general, so I am feeling a bit overwhelmed on what to try next.

Oh and "hi every one" /wave

---

### Post by oktob3r on 2008-05-20
i'm kinda in the same boat too... it displays the drives but i can't burn anything it always requests a disk be inserted when there already is and when i right click properties on the drive it says nothing can be found.

EDIT: When trying to use gnomebaker i get this error message

"wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
wodim: Cannot do inquiry for CD/DVD-Recorder.
Errno: 5 (Input/output error), test unit ready scsi sendcmd: fatal error
CDB:  00 00 00 00 00 00"

---

### Post by jkman on 2008-05-28
I have not tested this one to see if I still get the random unmounts, but the following link mentions removing a line from fstab.  I've done that and booted back into Hardy and my cd drive still shows up.  Hopefully it will not unmount on me.  I'll let you know.

[http://ubuntuforums.org/showthread.php?t=791366](http://ubuntuforums.org/showthread.php?t=791366)

---

### Post by student eternal on 2008-05-31
Hey I had a guru buddy of mine come over and we got my issue figured out, turns out it was a newbie issue, I had the CD drive temporarily unmounted when I upgraded to hardy and the fstab was not updated correctly and was displaying my cd0 device as /dev/hda I edited the fstab (in vi, a little intimidating when still new to Linux) to /dev/scd0 and the device immediately recognized.  

Hope this helps someone!

---

### Post by pouttu on 2008-06-02
Same problem here.
I dualboot with xp and just updated from 7.10 to 8.04 (amd64) and ever since, my dvd drive stopped working, although in windows it works just fine. Also i downloaded a kubuntu kde4 8.04 amd64 live cd and tried it, it showed the loadingscreen with all options (install, try, check cd) but then the cdrom stopped responding and i ended up in a terminal... this being the case its propably compatibility issue with 8.04 version? Help would be appreciated, although be warned im a beginner. Some nice piece of code that fixes everything would be well appreciated... :D

---

### Post by pouttu on 2008-06-03
Nevermind, i made a live usb and installed hardy from that, now the drive is working fine on a fresh ubuntu install ^^

---

### Post by jkman on 2008-06-07
I found the solution to my dvd issues:
[http://ubuntuforums.org/showthread.php?p=5136370#post5136370](http://ubuntuforums.org/showthread.php?p=5136370#post5136370)

---

