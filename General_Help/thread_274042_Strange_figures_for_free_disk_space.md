---
title: "Strange figures for free disk space"
date: 2006-10-09
forum: General Help
---

### Post by s_g_robertson on 2006-10-09
I have a second hard disk in my machine, it is 150GB  formatted using XFS, it is used purely for file storage and is mounted at /mnt/videodisk.  I ahve not been aware of any probelms previously, but after deleteing a good few GB's yesterday the file space does not appear to have been freed.
using df -h gives:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             7.4G  3.4G  3.8G  48% /
tmpfs                 126M     0  126M   0% /dev/shm
tmpfs                 126M   13M  113M  10% /lib/modules/2.6.12-10-386/volatile
/dev/hdc              149G  146G  3.8G  98% /mnt/videodisk

```

If i select the videodisk folder within nautilus and view it's properties then it reports that there are 114.8GB of files and free space of 3.8GB.  So something is not quite adding up.

Is free space not realeased immediately on this filesystem or do I have some other problem.

Any suggestions would be gratefully received.

Thanks

Stephen.

---

### Post by anaconda on 2006-10-09
Just like in windows the deleted files go to trash.. they aren't really deleted until you empty the trash.

I dont know how it is really supposed to be done, but I use the terminal.. I dont remember now (I am at work in windows :C  ) was it ".Trash" , or ".Lost and Found" but just go there and delete its contents..

I have noticed that when files are deleted using terminal they dont go to trash..

and you can see the hidden folders in nautilus by pressing Ctrl-h

---

### Post by s_g_robertson on 2006-10-09
Thanks for your reply but that is slightly different from the problem I am having, well I think it is.  

I have mainly deleted these files from a terminal, but if I do delete files from this disk using nautilus I get a dialog saying that they cannot be moved to the wastebasket but will be deleted immediately.  I'm not sure whether this is always the case with mounted disks or purely because there would not be enough space to move these files to .Trash on the disk that has the rest of the filesystem on.

Thanks

Stephen

---

