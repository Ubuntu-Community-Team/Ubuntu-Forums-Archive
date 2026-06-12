---
title: "ext3 Partition not mountable (after format with gparted)"
date: 2007-11-27
forum: General Help
---

### Post by Darkstriker on 2007-11-27
Hi folks,

My problem is as follows:
My Gnome Partition manager didn't work. It got stuck at Scanning all devices (it still does if i open it regularly). Anyways I found a workaroung for that by using ```
sudo gparted /dev/hda
``` in the terminal.

When I then unmounted my NTFS partitons Gparted crashed.
However, they still could be mounted etc so I didn't worry too much about that.
Then I deleted 2 partitions inside an extended partition and formatted those in ext3.
Gparted said it successfully formatted it and I did a quick reboot. My other ntfs drive still shows up perfectly.

Now my problem is:
On Computer I see an extra drive which is labelled ```
43.4 GB Volume
``` (which really is just the size of the partition) and all the other partitions and devices show up normally and work.

Now I try to mount that device. No success.
I used the following settings:
```
Mount Point: /media/hda3
File System: ext3
Mount options: rw nosuid nodev noatime user_id=0 group_id=0 default_permissions allow_other
```

and when mounting I get:
```
Cannot mount volume.
mount_point cannot contain the following character: newline, G_DIR_SEPARATOR (usually /)
```

Only with an OK button.

Something extra: In media hda5 en hda6 which were the mount points of the part of the extended partition which I deleted still show up and I got no clue why...

Any Ideas?

Thanks a lot in advance and I really hope you ppl can help me =)

Greetz
Darkstriker

---

### Post by Darkstriker on 2007-11-27
If I try to mount via the terminal i get:
```
user@computer:~$ sudo mount /dev/hda3
mount: can't find /dev/hda3 in /etc/fstab or /etc/mtab
```

Any clues?

---

