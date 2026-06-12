---
title: "Mounting windows &quot;partition&quot; from raid 0"
date: 2007-06-02
forum: General Help
---

### Post by gth740k on 2007-06-02
I'm trying to mount my windows drive(s) so i can access my files from ubuntu.  I'm using the ntfs-3g driver and config tool.  For reference, i have windows on a 2disk raid0 array, and ubuntu on a separate 3rd drive.  I think the problem is that my windows 'drive' is really 2 drives in raid 0.  When i run fdisk -l it shows both individual disks, but not one that represents the raid.  So every time i try to mount sda1 (the partition on the first drive in the raid0 array) i just get errors telling me stuff is courrupt. (sdb, the second drive in the array, shows up as having no partitions)     

Is it possible to workaround this, or is my only option to make a "windows" partition on my ubuntu drive and copy over the files i want to use?

---

### Post by phoenixnr on 2007-06-06
Having the same problem. Thought I could resolve by using paragons NTFS for linux which just resulted in more problems. Very frustrating. Anyone??

---

