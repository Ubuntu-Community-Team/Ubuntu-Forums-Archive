---
title: "Difficulty Mounting Hardrive to backup data using liveCD"
date: 2016-12-27
forum: General Help
---

### Post by dada55 on 2016-12-27
Hi Everyone,

My parents' laptop's crashed once and no longer boots. I found it was a hardrive failure by using dell's self diagnostic tool and now I am trying to backup the data using Ubuntu burned on a dvd. Unfortunately I am having some issues and need assistance please:

When i attempt to mount the hardrive (named as "OS" in file explorer) I get the following error:

[HTML]Error Mounting /dev/sda5 at media/ubuntu/OS: Command-line
'mount -t "ntfs"-o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999" "/
dev/sda5" "/media/ubuntu/OS"" exited with non-zero exit status 13:
ntfs_attr_pread_i:ntfs_pread failed: input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on 
Windows
then reboot into Windows twice. The usafe of the/f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/directory,
(e.g. 
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid'
documentation
for more details.[/HTML]

I found some previous people having this error using Terminal with: "sudo ntfsfix /dev/sda5". Running this in terminal returned:
[HTML]Mounting volume... OK
Processing of $MFT and $MFTMirr complted successfully.
Checking the alternate boot sector... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda5 was processed successfully[/HTML]

Which I thought was good news, but I still can't mount the hard drive and get the same error message.

Is there anything else I can do to try and backup the data on the hard drive? I think I got most of the data backed on an external harddrive but there is still some recent data that I would ideally want to recover if possible.

Many thanks for any suggestions!

---

### Post by oldfred on 2016-12-28
What version of Windows?
Windows 8 or later, uses fast start up or always on hibernation.
The Linux NTFS driver will not mount hibernated NTFS partitions.
It also will not mount partitions needing chkdsk. And running the ntfsfix, does not itself fix much but turns on the chkdsk flag so when Windows boots it will run chkdsk. And now you cannot default mount the NTFS.

You may be able to mount in read only mode (-o).
       mkdir /media/win
sudo ntfs-3g -o ro /dev/sda5 /media/win

---

### Post by dada55 on 2016-12-28
Hi oldfred, thanks for your reply, the laptop has Windows 10 so it could be hibernating. Is there any way I can stop it hibernating without booting windows, or what options do I have?  I tried to create a windows recovery usb from another windows 10 laptop, but for some reason it is extremely slow to load and keeps crashing at the point where I select keyboard layout.

---

### Post by oldfred on 2016-12-28
Did you try the read only mount?
And since chkdsk can only be run from Windows, did you run that when plugged into other Windows system.

---

### Post by dada55 on 2016-12-28
I did and it gave me the same error but within terminal:

[HTML]ntfs_attr_pread_i:ntfs_pread failed: input/output error 
Failed to calculate free MFT records: Input/output error
 NTFS is either inconsistent, or there is a hardware fault, or it's a 
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
 then reboot into Windows twice. The usafe of the/f parameter is very
 important! If the device is a SoftRAID/FakeRAID then first activate
 it and mount a different device under the /dev/mapper/directory, (e.g.
 /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
 for more details.[/HTML]

I was hoping to not have to connect it to other computers as I don't have the cables/adaptors but I guess there is no other way.

Thanks for your help

---

