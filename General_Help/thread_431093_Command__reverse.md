---
title: "Command  reverse"
date: 2007-05-02
forum: General Help
---

### Post by Jimmett on 2007-05-02
Hi Could someone please tell me how to reverse the action of the following command. Thanks in advance. ```
echo "none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0" | sudo tee -a /etc/fstab
```

---

### Post by qpwoeiruty on 2007-05-02
You can always:
```
sudo gedit /etc/fstab
```
and remove the last line from fstab (that's what your command does- add the line on the left to the end of /etc/fstab)

---

### Post by Jimmett on 2007-05-03
Thanks qpwoeiruty.

---

