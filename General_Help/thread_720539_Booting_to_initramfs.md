---
title: "Booting to initramfs"
date: 2008-03-10
forum: General Help
---

### Post by feest on 2008-03-10
hey guys,

After having gutsy hang on me just now (after being locked for a long time it wouldn't log back on, ctrl alt f1 didn't work, it just stayed translucent black, only mouse cursor would move) I rebooted and now the system loads ubuntu (the bar appears, doesn't seem to be loading) and then goes straight to buzybox

Can someone tell me why this is happening and how I can fix it? :(

```

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter &#8216;help&#8217; for a list of built-in commands.

(initramfs

```

---

### Post by pointone on 2008-03-10
It should display some sort of error message right above the BusyBox prompt. Please post it here.

---

### Post by feest on 2008-03-11
Well, it doesn't always show an error, but if I reboot a few times I do see this one come by:

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [     27.224000]  /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c:  usb_submit_urb(ctrl)  failed 
```

That's all it says then...

Booting it in safemode gives me these errors (in order of appearance):

```
mount: Mounting /dev/disk/by-uuid/b8a9cae0-cc25-477c-a33f-cc8d2be8077f on /root failed: Device or resource busy

and

mount: Mounting /root/dev/ on /dev/.static/dev failed: No such file or directory

and

mount: Mounting /sys on /root/sys failed: No such file or directory

and 

mount: Mounting /proc on /root/proc failed: No such file or directory

and

Target filesystem doesn't have /sbin/init
```

---

### Post by pointone on 2008-03-11
It looks like your fstab may contain errors. Try running "cat /etc/fstab" from the BusyBox prompt. If it fails, you'll need to boot in the live CD and mount your root partition from there to check the fstab.

---

