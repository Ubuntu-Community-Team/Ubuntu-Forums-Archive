---
title: "File size limit exceeded (core dumped) on mounted smb drive"
date: 2007-03-06
forum: General Help
---

### Post by jaredo on 2007-03-06
Hi,

I've recently installed the latest version of edgy.  I mounted two NAS devices using smb as per the user guide.  Excerpt from fstab:

//ip/public    /mnt/zen smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0
//ip/public    /mnt/slave smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0

When copying large files (~5GB ie. it could be a 4GB file limit) to the mounted disks, I receive this error:

File size limit exceeded (core dumped)

I've tried setting various ulimits to unlimited with no luck.

cheers,

Jared

---

### Post by Kateikyoushi on 2007-03-07
What filesystem do those NAS use ? Just because 4GB is the fat32 limit.

---

### Post by jaredo on 2007-03-07
They are NTFS.  It's probably worth adding that I have no problems moving >4GB files to and from using Windows file sharing.

---

### Post by asipi on 2007-04-24
linux smb implementation has a 2 or 4 GB filesize limit (depending on kernel version) that's sad :(

---

