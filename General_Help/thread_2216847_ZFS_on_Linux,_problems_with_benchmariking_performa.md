---
title: "ZFS on Linux, problems with benchmariking performance"
date: 2014-04-14
forum: General Help
---

### Post by kim_holmebakken on 2014-04-14
Hey all,
I have set up two ubuntuservers where one is a backend storage box containing a RAID1+0.
The other server is the frontend machine in which im trying to get zfs on linux to work properly on. For the storage availability im using a iSCSI initiatior/target setup. And the cache is an SSD.

I want this to be included into the pool im making, so that I have a complete storagebox.

On the frontend i did this for zfs:

```

[COLOR=#000000][FONT=Arial]zpool create -f -o ashift=12 pool /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdg cache /dev/sdb
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]zfs create -V 200G pool/brick0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]zfs create -V 200G pool/brick1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]zfs create -V 200G pool/brick2[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]zfs create -V 200G pool/brick3[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]zfs create -V 200G pool/brick4
[/FONT][/COLOR]
```

This resulting in having a /dev path to the different bricks.

I then ran this fio command (read):
```
[COLOR=#000000][FONT=Arial]fio --filename=/dev/pool/brick0 --fallocate=none --rw=randrw --refill_buffers --norandommap 
--randrepeat=0 --ioengine=posixaio --bs=4k --rwmixread=100 --iodepth=16 --numjobs=16 --runtime=60 --group_reporting --name=4krandreadtest[/FONT][/COLOR]
```

The results were astonishing, and I thought all is well.
However when I changed the command to do a rwmixwrite=100 instead of a rwmixread=100 the problems started comming.

The server freezes and cant allocate the testfiles in which fio will test on, and this renders the server useless.

Is there anyone that can see an error I have done and knows how to test the zfs pool with a write test instead og a read one ? Or in general knows (suspects) why the server freezes ?

And im running this setup on Ubuntu Server 13.10, where zfs is not /

Thanks in advance!

---

