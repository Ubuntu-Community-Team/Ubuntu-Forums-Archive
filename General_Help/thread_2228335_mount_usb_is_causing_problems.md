---
title: "mount usb is causing problems"
date: 2014-06-06
forum: General Help
---

### Post by sturmey2 on 2014-06-06
is there a way to mount a USB NTFS drive so that it has 777 permissions?
I used to be able to share these drives with an older computer that has Lubuntu 12 on it, but with Lubuntu 14 I can't.

yes I've already tried umask=000 but that didn't change anything.

---

### Post by rahul4557 on 2014-06-07
Check if the USB drive mounted doesn't have a read only option set while mounting.

---

### Post by sudodus on 2014-06-07
How do you mount the drive?

- completely automatically (without doing anything)
- automatically (after editing /etc/fstab)
- manually (by selecting it in a file browser)
- manually (with a command line)

Please describe what you do, and it will be easier to help.

---

### Post by Morbius1 on 2014-06-07
> **sturmey2 said:**
> is there a way to mount a USB NTFS drive so that it has 777 permissions?
I used to be able to share these drives with an older computer that has Lubuntu 12 on it, but with Lubuntu 14 I can't.
What do you mean by "share these drives"?

Share with other local login users or share with samba across the network? If it's a samba thing it's somewhat trivial to fix this.
> yes I've already tried umask=000 but that didn't change anything.
The difference between Ubuntu12 and Ubuntu 14 is the default mount point for these usb devices. 

In 12 the mount point was /media/LABEL. You could set permissions to 777 and all was good in the universe.

In 14 the mount point is /media/$USER/LABEL. /media/$USER is not under normal linux permissions but an ACL that restricts access to everything under it to $USER. It makes no never mind what the permissions on LABEL are since $USER gets in the way. If you are going to mount these yourself then you need to create another mount point ( might as well put it back where it belongs and set it to /media/LABEL ) and use umask=000 there.

---

