---
title: "Unable to mount imported DVD"
date: 2007-01-19
forum: General Help
---

### Post by perky on 2007-01-19
G'day!

I thought I'd picked up a bargin off Ebay, Unreal Tournament 2004 from overseas.  However, the DVD will not mount!  It works fine in Windows, but when it tries to mount in Ubuntu, I receive the following popup error:

```

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.
mount: block device /dev/hdc is write-protected, mounting read-only

mount: wrong fs type, bad option, bad superblock on /dev/hdc,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so

```

```

andy@andy-desktop:~$ dmesg|tail
[ 2957.449843] hdc: drive not ready for command
[ 2957.500266] hdc: ATAPI reset complete
[ 3017.695907] ide-cd: cmd 0x28 timed out
[ 3017.695912] hdc: DMA timeout retry
[ 3017.695914] hdc: timeout waiting for DMA
[ 3022.899807] hdc: status timeout: status=0xd0 { Busy }
[ 3022.899811] ide: failed opcode was: unknown
[ 3022.899838] hdc: drive not ready for command
[ 3022.951185] hdc: ATAPI reset complete
[ 3024.778073] Unable to identify CD-ROM format.

```

I have no problem mounting other CDs or DVDs.

My guess is that Ubuntu is having problems recognising this foreign DVD.

I could legally download the English DVD because I have a legit CD-KEY, but I'd rather be able to fix this problem rather than downloading a 3.6gb image!

Any ideas on how to get Ubuntu to recognise this DVD?

Thanks.

---

