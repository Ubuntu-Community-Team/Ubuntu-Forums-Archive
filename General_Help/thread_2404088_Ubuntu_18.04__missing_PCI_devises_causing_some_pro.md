---
title: "Ubuntu 18.04 : missing PCI devises causing some programs not to start"
date: 2018-10-19
forum: General Help
---

### Post by radaniba1 on 2018-10-19
Hello everyone

When I list bus/pci/devices I noticed I have a bunch of them towards the end that are missing

```
lrwxrwxrwx 1 root root 0 Oct 19 12:42 0000:00:16.3 -> ../../../devices/pci0000:00/0000:00:16.3
lrwxrwxrwx 1 root root 0 Oct 19 12:42 0000:00:1c.0 -> ../../../devices/pci0000:00/0000:00:1c.0
lrwxrwxrwx 1 root root 0 Oct 19 12:42 0000:00:1c.4 -> ../../../devices/pci0000:00/0000:00:1c.4
lrwxrwxrwx 1 root root 0 Oct 19 12:42 0000:00:1d.0 -> ../../../devices/pci0000:00/0000:00:1d.0
lrwxrwxrwx 1 root root 0 Oct 19 12:42 0000:00:1f.0 -> ../../../devices/pci0000:00/0000:00:1f.0
lrwxrwxrwx 1 root root 0 Oct 19 12:42 0000:00:1f.2 -> ../../../devices/pci0000:00/0000:00:1f.2
lrwxrwxrwx 1 root root 0 Oct 19 12:42 0000:00:1f.3 -> ../../../devices/pci0000:00/0000:00:1f.3
lrwxrwxrwx 1 root root 0 Oct 19 12:42 0000:00:1f.4 -> ../../../devices/pci0000:00/0000:00:1f.4
lrwxrwxrwx 1 root root 0 Oct 19 12:42 0000:00:1f.6 -> ../../../devices/pci0000:00/0000:00:1f.6
lrwxrwxrwx 1 root root 0 Oct 19 12:42 0000:02:00.0 -> ../../../devices/pci0000:00/0000:00:1c.0/0000:02:00.0
lrwxrwxrwx 1 root root 0 Oct 19 12:42 0000:04:00.0 -> ../../../devices/pci0000:00/0000:00:1c.4/0000:04:00.0
lrwxrwxrwx 1 root root 0 Oct 19 12:42 0000:06:00.0 -> ../../../devices/pci0000:00/0000:00:1d.0/0000:05:00.0/0000:06:00.0
lrwxrwxrwx 1 root root 0 Oct 19 12:42 0000:06:01.0 -> ../../../devices/pci0000:00/0000:00:1d.0/0000:05:00.0/0000:06:01.0
lrwxrwxrwx 1 root root 0 Oct 19 12:42 0000:06:02.0 -> ../../../devices/pci0000:00/0000:00:1d.0/0000:05:00.0/0000:06:02.0
lrwxrwxrwx 1 root root 0 Oct 19 12:42 0000:06:04.0 -> ../../../devices/pci0000:00/0000:00:1d.0/0000:05:00.0/0000:06:04.0
lrwxrwxrwx 1 root root 0 Oct 19 12:42 0000:3b:00.0 -> ../../../devices/pci0000:00/0000:00:1d.0/0000:05:00.0/0000:06:02.0/0000:3b:00.0
```

The 5 last directories are missing Any idea on how to fix this problem ? It is causing some programs to crash or not start at all
  Any idea ?

---

