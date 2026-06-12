---
title: "startup disk creator fail to erase usb stick"
date: 2013-03-09
forum: General Help
---

### Post by dvks on 2013-03-09
I am trying to use the startup disk creator, when I click on erase to cleanup the USB stick I get a long error "org.freedesktop.DBus.Error.NoRerply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken" any idea how to solve it or even understand the problem?

---

### Post by sudodus on 2013-03-09
Can you mount the usb stick? Please post the output of the following commands

```
sudo fdisk -lu
```
```
sudo blkid
```
and try to mount it with the file browser. Can you see any files? Can you write a new file or directory?
Finally post the output of
```
df
``` and ```
cat /etc/mtab
```

---

