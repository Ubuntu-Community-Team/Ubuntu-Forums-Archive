---
title: "Can't mount volume (ext4+luks)"
date: 2015-01-06
forum: General Help
---

### Post by andrea48 on 2015-01-06
Hi
after having a bad issue with my chromebook, i am trying to backup the files i have stored: i took off the ngff SSD HD and put it in a SATA/USB adapter.
The volume is fully encrypted with LUKS (ext4+luks) so when i try (after writing the correct passphrase) to access to the volume i get this error

The unlocked device does not have a recognizable file system on it

So what i can access is only a 255mb partition which contain these files:

[IMG]http://i58.tinypic.com/j5jcie.png[/IMG]


I tryed to mount the volume using (sdb5 is my encrypted volume)

```
sudo cryptsetup luksOpen /dev/sdb5 sdb5
```

and then

```
sudo mkdir /media/xxx
sudo mount /dev/mapper/sdb5 /media/xxx
```

but all i get is

```
mount: unknown filesystem type 'LVM2_member'
```

So, as seen [here]("http://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line?lq=1"), i tryed (now the volume is sdc5, dunno why)

```
sudo udisksctl unlock -b /dev/sdc5


```

getting

```
Unlocked /dev/sdc5 as /dev/dm-4
```

then

```
udisksctl mount -b /dev/mapper/ubuntu-root
```

but having

```
Error looking up object for device /dev/mapper/ubuntu-root


```

here is how the disk manager see my 16gb HD (i have never seen 3 "partion", usually when i encrypt a volume there is only 2)

[IMG]http://i62.tinypic.com/2j4x7km.png[/IMG]

I also used [this guide]("http://blog.gnu-designs.com/solved-howto-mount-an-external-encrypted-luks-volume-under-linux/"), but all i have got is

```
missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```


**TLDR **i can't mount an external fully encryopted (with LUKS) HD because " The unlocked device does not have a recognizable file system on it"



Any idea on how can i access my data??
Thanks

---

### Post by andrea48 on 2015-01-19
Anyone?

---

