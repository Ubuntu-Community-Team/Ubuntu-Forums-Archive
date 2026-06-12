---
title: "Can't find other partitions"
date: 2015-04-02
forum: General Help
---

### Post by tigerprowl6 on 2015-04-02
I just installed the latest Kubuntu but now I can't see the folders to get to files I saved in Windows.

---

### Post by Mark Phelps on 2015-04-02
Are you dual-booting with Windows and Kubuntu on the same PC?

IF so, which version of Windows are you running?

What happens when you try to see the files?

---

### Post by tigerprowl6 on 2015-04-03
Windows 7, worked before with previous Ubuntu versions.
I can't see the folders, so I can't see the files.  Usually the hard drives are listed on the left in the File Manager window.

---

### Post by sotiris2 on 2015-04-03
Please give us the output of the following command ```
sudo blkid
``` ```
sudo parted -l
```

---

### Post by tigerprowl6 on 2015-04-03
Audio also stopped working after it restarted, so I reinstalled Kubuntu and chose not to allow Kubuntu to install extra stuff.  Maybe there was a conflict.  In addition, files were not downloading in the software center.  I installed it manually, not sure if this also may have resolved the issue.  The only thing now is some sites don't stream video as well as in Windows, but I'll live with it until I can reformat the whole hard drive.

---

