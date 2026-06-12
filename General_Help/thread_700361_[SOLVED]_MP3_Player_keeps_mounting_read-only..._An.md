---
title: "[SOLVED] MP3 Player keeps mounting read-only... Any help?!"
date: 2008-02-18
forum: General Help
---

### Post by geo909 on 2008-02-18
Hello everybody.
Could you please help me with that?
As the title says, I have an MP3 Player who keeps mounting in read-only mode. ](*,)
It is a UNITED 256MB player..

Err.. What else?
That's my fdisk -l when only the MP3player is connected:

```
jorge@jorge-desktop:~$ fdisk -l
Note: sector size is 2048 (not 512)

Disk /dev/sdc: 268 MB, 268435456 bytes
16 heads, 57 sectors/track, 143 cylinders
Units = cylinders of 912 * 2048 = 1867776 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         144      261056    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(755, 15, 0) logical=(143, 2, 29)
Partition 1 does not end on cylinder boundary.
jorge@jorge-desktop:~$ 

```

Sorry for not giving any more info, I don't really know what else is needed.
Any ideas? Any additional info needed?

Please, help me. This is so frustrating, I have to open windows as root and also amarok can't write to the device...
Thanks in advance!

[B]
EDIT:
[/B]   Another strange thing is that the player also mounts read-only even if I do:
>  sudo mount -o rw /dev/sdc1 /media/sdc1

ANd there is no protection or something on the disk..

---

### Post by PmDematagoda on 2008-02-18
Did you do an fsck check on the device to ensure that there aren't any problems with it?

First unmount the player using:-
```
sudo umount /media/sdc1
```

Then check the filesystem using:-
```
sudo fsck /dev/sdc1 -r
```

---

### Post by geo909 on 2008-02-18
Well (strange!) I think I found the problem:
Inside the .Trash folder of the disk, there was another .Trash folder from another disk I had (don't ask how it got there)!!
The thing is that every time I was trying to delete the .Trash inside the .Trash, the disk turned to be readonly. That was also the case if I was asking to empty the trash bin. I did a format and now it acts OK!

Now there is another problem, but I will post it on a new tread cause it is of a different nature.

Thanks a lot for your time!

---

