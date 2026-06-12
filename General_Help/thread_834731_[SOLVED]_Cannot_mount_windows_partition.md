---
title: "[SOLVED] Cannot mount windows partition"
date: 2008-06-19
forum: General Help
---

### Post by siebesadeq on 2008-06-19
****Is there anybody who can help?...****
I've just installed Hardy Heron on my mother's computer and can't mount the windows partition.
She used to have 2 partitions in windows; 1 for the program files (drive c) and 1 for her personal data. I deleted drive c and installed Ubuntu there, and kept drive d. Now when I try to mount it I get the error message that it cannot be mounted because it wasn't shut down properly. As you can see, I cannot restart windows because I don't have it anymore. So how can I mount the drive d? Please help me if you can.

---

### Post by iaculallad on 2008-06-19
Try to force mount the windoze partition. Better yet, try to post the error message that displays when you mount the partition so we know what to force mount.

---

### Post by siebesadeq on 2008-06-19
Thanks for your reply. Unfortunately I'm not at the computer in question at the moment, but I will follow your advice when I get there.

---

### Post by VMC on 2008-06-19
> **siebesadeq said:**
> ****Is there anybody who can help?...****
I've just installed Hardy Heron on my mother's computer and can't mount the windows partition.
She used to have 2 partitions in windows; 1 for the program files (drive c) and 1 for her personal data. I deleted drive c and installed Ubuntu there, and kept drive d. Now when I try to mount it I get the error message that it cannot be mounted because it wasn't shut down properly. As you can see, I cannot restart windows because I don't have it anymore. So how can I mount the drive d? Please help me if you can.


Since you don't have Windows anymore. You need to find a NTFS boot disk. Either floppy or cd, the has checkdisk on it.

Edit: here's one site that does:[http://www.bootdisk.com/ntfs.htm](http://www.bootdisk.com/ntfs.htm)

---

### Post by ktrnka on 2008-06-19
Have you tried ntfsfix?

```
sudo ntfsfix /dev/yourdeviceandpartition
```

Otherwise I would force mount it like iaculallad suggested

---

### Post by siebesadeq on 2008-06-19
Thanks for your reply. Unfortunately ntfs4dos is of no use to me, as I don't use windows anymore

---

### Post by siebesadeq on 2008-06-19
Thank you too for your suggestion Ktrnka. will try that too

---

### Post by siebesadeq on 2008-06-19
OK, I'm at the computer now. I've tried to force mount the volume, but was unsuccessful. I get the following error message, when I try to mount the volume (see attachment):

---

### Post by iaculallad on 2008-06-19
In your terminal:

```
sudo mount -t ntfs-3g /dev/sda5 /media/DATA -o force
```

---

### Post by siebesadeq on 2008-06-19
I get the following error:
sudo mount -t ntfs-3g /dev/sda5 /media/DATA -o force
fuse: failed to access mountpoint /media/DATA: No such file or directory

---

### Post by iaculallad on 2008-06-19
In your terminal:

```
sudo mkdir /media/DATA
sudo mount -t ntfs-3g /dev/sda5 /media/DATA -o force
```

---

### Post by siebesadeq on 2008-06-19
Wherever you are, whoever you are. you're a life saver! Thank you very much!!!

---

### Post by iaculallad on 2008-06-19
You're welcome. Go Ubuntu

---

### Post by Bucky Ball on 2008-07-08
In my case, I clicked Vista partition, was told could not mount and on the error splash screen, I opened the details tab and it gives me two options, the second you mentioned.

It seems to be about (for me at least and could be for some others with the dual boot MS OS) an unclean shutdown of my Vista OS. The first option advises me to boot Vista, clean up and shutdown cleanly. I'll go back and try that, see what happens, but do remember about 6 months ago getting the same problem one day. Option 1 worked in my case.

Cheers and yea, love Ubuntu more now that Hardy has my wireless working!
Hardy 8.04, HP dv6000 series lappy.

---

