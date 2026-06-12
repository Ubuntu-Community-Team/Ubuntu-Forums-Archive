---
title: "making grub the bootloader again"
date: 2007-02-16
forum: General Help
---

### Post by z987k on 2007-02-16
Is there a way to write over m$'s bootloader with grub after the windows bootloader has written over grub?  Cause now I can't boot to ubuntu after installing windows on a small partition.  I would think I could just use the livecd to put grub back on there, but what would the command for that be?

---

### Post by alyoung on 2007-02-16
If you boot using the LiveCD, you can run the command 'grub'.

You will then get a prompt similar to that below:

```
grub>
```

Perform the following commands:

```
grub>  find /boot/grub/stage1
grub> root (hd0,0)
grub> setup (hd0)
```

Assuming you are installing to the boot sector of the first drive, and on the first partition. It won't be the first partition, as you have Windows, but you should be able to work out which partition it is - this will the reflected in a change in the second '0'.

Before executing grub, you'll need to give the command 'sudo -i'

---

### Post by meng on 2007-02-16
This is also mentioned in:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by z987k on 2007-02-16
Thanks!

---

