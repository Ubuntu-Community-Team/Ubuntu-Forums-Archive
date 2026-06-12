---
title: "Bizarre Directory Mapping Issue?"
date: 2006-07-10
forum: General Help
---

### Post by Ted_Smith on 2006-07-10
When I look at the root tree of my Ubuntu installation, there's a directory called dev/disk/by-uuid. In there are files (mostly of zero bytes) relating to attached media that I am very interested in (for reasons outside the scope of this). Specifially the fact that when a device is plugged in and then unmounted and removed a file is created then deleted. 

However, when I take the disk out of the machine and connect ceretain software to look at the disk, the dev folder does not have a 'disk' subdirectory. In fact, the only sub-directories that actually exist (in accordance with the mapping of the filesystem) is dev/pts and dev/shm. 

So, I assume that when my Ubuntu system is on, what I am seeing is a 'virtual' set of folders setup as perhaps a RAMDisk or something? 

Can anyone help me understand why the folders are there normally, but not when the disk is looked at in isolation from the computer?

Thanks

Ted

---

### Post by Ted_Smith on 2006-07-11
OK, is there perhaps a useful resource or web site that some could recommend to me that may help me to determine it for myself, assuming no one knows? 


Could this be one of those things that I'd need to ask a developer? 

If it helps, it's for the purpose of law enforcement and research I am doing as part of that. 

Cheers

Ted

---

### Post by nanotube on 2006-07-11
i'm not a linux filesystem guru by any means, here's what i can tell you. first, look at the output of your "df" command. here's mine:
```

nanotube@groovy4:[~]$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdc3              9629912   4996024   4144712  55% /
varrun                  387348       104    387244   1% /var/run
varlock                 387348         0    387348   0% /var/lock
udev                    387348       128    387220   1% /dev
devshm                  387348         0    387348   0% /dev/shm
lrm                     387348     18316    369032   5% /lib/modules/2.6.15-25-686/volatile
/dev/hdc1             10241404   5266000   4975404  52% /mnt/win
/dev/hdc5             18570048   9140704   9429344  50% /data

```
you can notice that /dev is a separate mount point, and some filesystem "udev" is mounted on it. so, we will "man udev", and we get a long manpage, but the following sentence clears it up:
> udev provides a dynamic device directory containing only the files for actually
       present devices. It creates or removes device node files in the /dev directory, or it
       renames network interfaces.

so, to summarize, /dev is a dynamic filesystem, that is recreated every boot, and is managed dynamically. 

hope that answers some of your questions. :)

---

### Post by Ted_Smith on 2006-07-13
That's fantastic - thank you so much. I had suspected it was some kind of virtual\dynamic process but your clarification 'proves' it. 

Thanks again

Ted

---

