---
title: "Can't create file on external USB drive."
date: 2020-05-01
forum: General Help
---

### Post by rsteinmetz70112 on 2020-05-01
I have and external USB drive I am trying to use backup files and move them to another site.
I was using rsync to transfer the files to the drive and part through the transfer I started getting errors like this:
```

rsync: mkstemp "/mnt/files.bak/Office/arris.lucretia/arris/done/ar.FrankDarby/db.circuitc/.dl.CCclgtxCD.DJxYaz" failed: Input/output error (5)
```

CDing to that directory I find I cannot create a new file. 

The Drive is a Seagate BAsic and has an NTFS file system.
I tried fixntfs and no luck

---

### Post by CelticWarrior on 2020-05-01
Was the drive previously used in any Windows 8 or newer with the default Fast Startup feature turned on?
If so it's in "read-only" mode due to that feature.

If the drive is *not *intended to be shared with any Windows system then it's better to reformat it as EXT4.

---

### Post by ActionParsnip on 2020-05-01
Why are you using NTFS?

---

### Post by rsteinmetz70112 on 2020-05-01
It was not used on any Windows 8 or newer. It was only used on Linux.
I was able to transfer many GB of date before it stopped accepting new files.
The drive is 2 TB

---

### Post by rsteinmetz70112 on 2020-05-01
Thats the way it came. Since I was only doing it for a limited operation I didn't reformat.

---

### Post by TheFu on 2020-05-01
NTFS with rsync won't keep the permissions, owner, group, ACLs, and xattribs that a native Linux file system would retain.  

For pure data, owned by a single userid, that might not matter. 

For settings, crypto files (keys) and system level backups, that just won't work. You'll have a false sense that you can restore, but the restore won't work. Sure, the files will be put back, but without all the permissions et al, they won't be useful.

Plus, NTFS supports different file names than Unix/Linux, so some of the filenames are likely to be mangled.

If you have to use NTFS, then you'll need to use a backup tool like duplicity, or something based off it, that captures all those extra things in separate files that get included as all the chunked backup files.  Duplicity is amazing, but has some issues. All backup tools seem to have at least one problem that we need to live with or mitigate.

---

### Post by rsteinmetz70112 on 2020-05-05
OK I hooked it up to a Windows computer and ran chkdsk, and the seemed to work but I decided to be safe I'd reformat the drive as ext4. 
That went fine but once the drive was reformatted I got an error message that the kernel wouldn't recognize the drive. Checking the drive showed the old partition information although fdisk showed the new information. Rebooting fixed it and the new filesystem was present. However there must be some way to get the kernel to recognize a reformatted external drive.

---

### Post by ActionParsnip on 2020-05-05
If its only to be used in Linux, use a Linux file system

---

### Post by TheFu on 2020-05-05
[LIST]
[*]Sometimes HDDs fail.  Does the SMART data have any clues?
[*]How is is connected? USB?  Have you tried using a different USB port and different USB cable?
[*]Are there any know issues with the drive controller being incompatible?
[*]Files that are open for exclusive use on the source can cause problems when being copied. The only certain way is to boot from alternate media so the source partitions aren't being used.
[*]Which new file system do you create?
[/LIST]
We can't read thoughts. Need the info.

I searched for "Seagate BAsic linux" and didn't find anything.  Nothing found any Seagate "Basic" model either.

---

### Post by rsteinmetz70112 on 2020-05-05
> **TheFu said:**
> [LIST]
[*]Sometimes HDDs fail.  Does the SMART data have any clues?
Doesn't seem to work over USB. I did try smartclt and got some information which generally looks OK, but I didn't run a full test 
 [*]How is is connected? USB?  Have you tried using a different USB port and different USB cable?
USB3 I've tried multiple ports on different computers.
[*]Are there any know issues with the drive controller being incompatible?
Not that I know of
[*]Files that are open for exclusive use on the source can cause problems when being copied. The only certain way is to boot from alternate media so the source partitions aren't being used.
The files should have been unused. They were data files and there were no other users active.
[*]Which new file system do you create?
ext4 and it's working once I rebooted.
[/LIST]
We can't read thoughts. Need the info.

I seldom use external USB drives, I can't remember last time I reformatted one, but I found it odd that the reformated drive needed a reboot to be properly recognized. 

I searched for "Seagate Basic linux" and didn't find anything.  Nothing found any Seagate "Basic" model either.

That is how it's identified internally by Gnome Disks and smartctl. 
The Label says "SEAGATE Basic Portable Drive". the Part Number is 2URAP4-500 Model SDRD0NF1

---

