---
title: "[SOLVED] Virtualbox writing straight to hard disk."
date: 2007-09-09
forum: General Help
---

### Post by Frak on 2007-09-09
Is there any way for Virtualbox to write to HD like VMWare can (Virtual HD = Physical HD)?

Thanks for the help.

EDIT
Never Mind, I got it working
For the record
```
VBoxManage internalcommands createrawvmdk -filename /path/to/file.vmdk  -rawdisk /dev/sda
```

Hope that helps anybody else :)

---

