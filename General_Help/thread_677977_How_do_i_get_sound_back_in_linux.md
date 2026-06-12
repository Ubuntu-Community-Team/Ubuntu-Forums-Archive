---
title: "How do i get sound back in linux?"
date: 2008-01-25
forum: General Help
---

### Post by ele_mugv on 2008-01-25
I installed linux after i installed vista...the sound plays in vista but not in linux..it shows it's playing but i hear nothing from the speakers (i tested the speakers separately to make sure they r working). Pls help¿

---

### Post by ajgreeny on 2008-01-25
Have you checked the volume of everything in the volume control on the taskbar?  Perhaps something is set too low.

---

### Post by ugm6hr on 2008-01-25
First thing - let us know what sound card you have (post the output from this command):
```
lspci | grep Audio
lshw -C multimedia
```

Assuming the driver modules are installed OK - it is likely you just have to unmute & maximize volumes in alsamixer:
```
alsamixer
```

[http://ubuntuforums.org/showpost.php?p=2763743&postcount=9](http://ubuntuforums.org/showpost.php?p=2763743&postcount=9)

---

### Post by xeth_delta on 2008-01-25
You might be interested in reading this: [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449"), the "Comprehensive Sound Problem Solutions Guide v0.5e".

Xeth

---

