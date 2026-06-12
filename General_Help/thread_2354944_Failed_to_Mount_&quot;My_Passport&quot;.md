---
title: "Failed to Mount &quot;My Passport&quot;"
date: 2017-03-07
forum: General Help
---

### Post by Rick St. George on 2017-03-07
Received the following Error, after CLONEZILLA (Nov.2016 Yakkety) crashed while making a Backup. My 2TB Passport opened fine in Win7.

> 
Error mounting /dev/sdd1 at /media/stephen/My Passport: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdd1" "/media/stephen/My Passport"' exited with non-zero exit status 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdd1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details.


Any idea what is going on???
Thanks!
Rick
):P

---

### Post by howefield on 2017-03-08
> **Rick St. George said:**
> In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details.

Just to clarify, it's not clear if you did as the error suggested ?

---

### Post by Rick St. George on 2017-03-08
SORRY: Don't know if this is the right thread or not?!

Howefield wrote: 
> Just to clarify, it's not clear if you did as the error suggested ?

Didn't think I had to ... it came up on my Win7 laptop. So I thought it was OK. Plugged back into my main sys with UbuntuStudio v16.04 and received the Error again. Don't understand what the problem is?!?!? By the way, CloneZilla failed while backing up my Samsung SSD drive.

---

### Post by SeijiSensei on 2017-03-08
You probably need to connect the drive to a Windows machine and run chkdsk against it.  Unless you have a need to share data between Windows and Linux on the same machine, in a "dual-boot" arrangement, there's no reason to have any NTFS file systems.  If we're only talking about using the with Linux systems, I'd reformat the drive to ext4.  If you have to have NTFS, then any problems with the integrity of the filesystem will need to be fixed with Windows chkdsk.

---

### Post by Habitual on 2017-03-08
Dirty Shutdown, or *RAID* as explained.

---

### Post by Rick St. George on 2017-03-08
Thanks Sensei,  Started that before reading your reply. Win7 did find some problems and fixed them. In addition I'm running Defrag, but it will take awhile on 2TB drive... still running. I will consider this closed.

But here may be a fix to problem. In a semi-related issue, regarding overheating and shutting down while using CloneZilla, Steven Shiau over at SourceForge had this to say (see end of thread this post: [https://sourceforge.net/p/clonezilla/discussion/Help/thread/01f9d1ea/?page=1](https://sourceforge.net/p/clonezilla/discussion/Help/thread/01f9d1ea/?page=1))

> [LEFT][COLOR=#555555][FONT=sans-serif]Normally this is related to hardware issue, especially the heat issue. Clonezilla DOES work for multi-core CPU machine.[/FONT][/COLOR]
[COLOR=#555555][FONT=sans-serif]If you enter expert mode, and choose the compression as "-z1" (not -z1p), then it will use only one core to compress the image. Maybe it won't cause high temperature so your machine won't shutdown.[/FONT][/COLOR][/LEFT]

FYI - in case anyone else runs into the same problem.
Thanks for being there everyone!

Peace,
Rick

---

