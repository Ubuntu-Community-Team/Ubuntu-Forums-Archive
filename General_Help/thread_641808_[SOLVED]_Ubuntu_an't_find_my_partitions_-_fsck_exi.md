---
title: "[SOLVED] Ubuntu an't find my partitions - fsck exit status 24, UIDs"
date: 2007-12-15
forum: General Help
---

### Post by Shampyon on 2007-12-15
I finally found a game worth having a Windows partition again for: Portal. After I'd finished Half Life 2 Episode 1 i got rid of my Windows partition, thinking it'd be a long time before I needed one again.

Well I've managed to reinstall windows on a separate SATA drive and get GRUB working. The problem was, I started getting this error: ***fsck died with exit status 8***. It would sit in the terminal until I typed ***shutdown now***, whereupon it would finally go to the Ubuntu login. Once logged in, I saw that Ubuntu couldn't see my other Linux partitions any more, although it was recognising the separate Windows drive.

I read that one possible solution to this was to delete the UIDs from FSTAB, so I did. This time instead of the previous error I got ***fsck died with exit status 24***. I know this means it's a combination of other errors, but what i don't know.[B]

[SIZE="4"]Anyway, to cut a long story short[/SIZE]:[/B]

Is there any way to get Ubuntu to recheck both my drives and their partitions to make a new fstab?
Until I can fix this problem I'm unable to access a few dozen gigabytes of personal data.

EDIT: using *sudo vol_id -u device* I got the current UIDs for my partitions and saved them to fstab. I'm now getting *fsck has died with exit staus 16*, which is apparently a syntax error. This is my current fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=73df2d01-723f-42d3-ad31-681bdbc3e81b /media/sdb1     reiserfs defaults        0       2
# /dev/sdb5
UUID=8a3a9f51-7010-4bbe-8f07-40d4b2e6f6d3 /media/sdb5     reiserfs defaults        0       2
# /dev/sdb6
UUID=9e3a4932-795c-41e4-b96a-4c33ba032c74 /media/sdb6     reiserfs defaults        0       2
# /dev/sdb7
UUID=e35621df-059d-4288-b99c-8917ba917848 /media/sdb7     reiserfs defaults        0       2
# /dev/sdb8
UUID=e6df3e16-1257-46a8-aa93-2718b84102a4 /media/sdb8     reiserfs defaults        0       2
# /dev/sda9
UUID=d74e56d7-6a52-4ec9-bfeb-b9f9bec5ed99 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

---

### Post by Shampyon on 2007-12-16
Update: It seems the partitions are mounted. I've been able to access them. However they aren't appearing under **Places** or **Computer**. Very odd. Also, the **fsck** error is still present at startup.

---

### Post by Shampyon on 2007-12-17
i was wrong about the partitions being mounted. At least, wrong about them being auto-mounted. I used *sudo mount -a* to mount them after boot (I'm still getting the same errors.) I've changed* /dev/partition* to */media/partition* and added my windows partition in fstab. I have no idea if I'm doing this right. I'll post the results later.
[B]
UPDATE: Solved?[/B]

Going through fstab I noticed one major mistake. I typed my home partition's mount point at "*/media/sdb1*". Obviously this is supposed to be simply "/" Once I corrected that, my Ubuntu partitions automounted just like they did before the XP Reinstall.

I hope this record of my trial and error can help any of you who have similar troubles.

---

