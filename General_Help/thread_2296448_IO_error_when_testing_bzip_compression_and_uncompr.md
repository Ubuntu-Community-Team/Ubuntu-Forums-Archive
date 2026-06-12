---
title: "I/O error when testing bzip compression and uncompressing bz2 file"
date: 2015-09-25
forum: General Help
---

### Post by cobalt2 on 2015-09-25
This is the terminal output I'm getting:
```
obalaban@obalaban:/mnt/Backup Disk/09242015$ bzip2 -tv 09242015.tar.bz2
  09242015.tar.bz2: 
bzip2: I/O or other error, bailing out.  Possible reason follows.
bzip2: Input/output error
    Input file = 09242015.tar.bz2, output file = (none)
obalaban@obalaban:/mnt/Backup Disk/09242015$ bunzip2 09242015.tar.bz2

bunzip2: I/O or other error, bailing out.  Possible reason follows.
bunzip2: Input/output error
    Input file = 09242015.tar.bz2, output file = 09242015.tar
bunzip2: Deleting output file 09242015.tar, if it exists.
```
The tar.bz2 file is 39.2 GB on a 313 GB NTFS partition. I was able to perform these tasks on this partition before, so I don't think the NTFS file system is a problem.

---

### Post by tgalati4 on 2015-09-25
Perhaps there is a 32 GB limitation somewhere.  Try reducing the dataset to 32 GB and try again.  If it succeeds then you have found a bug or a limitation.

Look at *dmesg*:

```
dmesg | tail -50
```

If you have any disk IO errors then check the SMART status of the disk drive.

---

### Post by cobalt2 on 2015-09-27
I ran an extended SMART self test on the volume, and the assessment was "self test failed." What does this mean? Is the hard drive about to fail?

---

### Post by tgalati4 on 2015-09-27
Yes.

Post the output of:

```
sudo smartctl -a /dev/sda
```

Back up your important data.  

NOW.

---

