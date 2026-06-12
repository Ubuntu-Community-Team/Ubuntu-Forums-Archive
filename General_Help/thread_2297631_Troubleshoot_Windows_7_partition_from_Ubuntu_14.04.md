---
title: "Troubleshoot Windows 7 partition from Ubuntu 14.04, dual boot"
date: 2015-10-05
forum: General Help
---

### Post by techee12 on 2015-10-05
Previously working dual boot, Windows 7, Ubuntu 14.04.3, not a boot issue. I want to use my Ubuntu to troubleshoot a Windows problem. I wish to run disk check, and possibly Clam TK from the Ubuntu terminal, on the Windows partition. I would not even bother with Windows, but I must use it for some work related jobs. Will someone help me to run these checks from the Ubuntu terminal? Thank you.

---

### Post by SeijiSensei on 2015-10-05
I would only run chkdsk from Windows. See [this](https://help.ubuntu.com/community/FilesystemTroubleshooting#ntfs-3g_.28previously_also_ntfsprogs.29_-_NTFS_filesystem).

For antivirus, install clamav, mount the Windows partition, then run
```
sudo clamscan -r /path/to/the/windows/partition
```

---

### Post by techee12 on 2015-10-05
Thank you, that's why I love the Ubuntu community. Does anyone know of tutorials using Ubuntu to troubleshoot the Windows partition?

---

### Post by Bucky Ball on 2015-10-05
Have you tried fixing Windows with the recovery media? I think there is a repair option on that. Might be a silly suggestion, but ...

What exactly is the Windows problem you want to troubleshoot?

---

### Post by techee12 on 2015-10-05
Thanks, I will get back this evening regarding the details of Windows problem. It began wanting to boot in safe mode, now won't boot at all in Windows.

---

