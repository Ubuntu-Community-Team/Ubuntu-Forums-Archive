---
title: "[SOLVED] NTSF or FAT32"
date: 2007-12-03
forum: General Help
---

### Post by valleyman7 on 2007-12-03
Can Ubuntu or Xbuntu be installed on an IDE ATA hard drive that is formated to NTFS? The hard drive was FAT32 and when I formated it I set it to NTFS and now Linux doesn't see the drive. If I was supposed to leave the drive at Fat32 is there a way to get it back. TIA :confused:

---

### Post by atlfalcons866 on 2007-12-03
ntfs can be read and written to using ntfs-3g
fat32 has full read/write support.

you can only boot on native linux file systems (ext2,ext3,reiserfs,jfs,xfs)

---

### Post by uPilot on 2007-12-03
As mentioned, ntfs-3g is ideal for mounting NTFS partitions/drives in read/write.  But you really dont want to make it, or FAT32 as anything essential to your Linux.

Best use ext3/ext2

---

### Post by valleyman7 on 2007-12-03
I have no clue what ntfs-3g is If I can convert back to Fat 32 will I be OK? I am not that computer savey. Smart:)

---

### Post by merlinus on 2007-12-03
ntfs-3g is a driver (now included with gutsy) that allows read/write to ntfs-formatted drives.

```

sudo apt-get install ntfs-config

```

Then

```

sudo ntfs-config

```

Tick the appropriate boxes and restart.

IIRC, you cannot go back to fat32 after changing to ntfs.  In any event, best to back up important data first.

---

### Post by -grubby on 2007-12-03
well you can't boot Linux on any non-linux filesystems, so formatting it to NTFS and then back to FAT32 or whatever is kinda pointless

---

### Post by valleyman7 on 2007-12-03
:mad::mad: Looks like the hard drive has gone south. I can see it and format it in the xp computer mgr, but it will not let me install even xp on it. I was going to install xp on it and select fat32 as was suggested. I tried to run spinrite and it would boot but like all my other tools they could not detect it.Time to order a new HD from Newegg I guess I was wondering what I was going to buy for christmas :confused:

---

### Post by valleyman7 on 2007-12-05
Well it looks like the hard drive went bad, but, it is the strangest thing I have seen in all my years of computing. Note many years of computing but just not a lot of technical know how. Computer mgmt says the drive is healthy I can format it install to it and just about anything I want to do as long as it is in the USB enclosure. As soon as I install the hard drive in my Inspiron 9300 it's not recognized. I have run the Segate Sea Tools, chkdsk /r and I tried to use tools with UBCD and spin rite. All of these tools to include trying to install windows XP Pro cannot recognize it. I guess as it is still new I will try to see if I can send it back to Segate/Maxtor and maybe they will replace it. I am curious if anyone has ever en-counted this problem and might have a suggestion how to revive the drive. I have considered a low level format but that might void the warranty.  I would appreciate any suggestions or feed back. I have now installed Ubuntu 7.10 on another computer for the time being. Thanks in advance:confused:

---

