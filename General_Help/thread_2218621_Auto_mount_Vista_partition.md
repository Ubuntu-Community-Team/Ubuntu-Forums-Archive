---
title: "Auto mount Vista partition"
date: 2014-04-21
forum: General Help
---

### Post by poliltimmy on 2014-04-21
This is my fstab. I configured sda1 with ntfs-config. I should not have done that. It now mounts Vista partition on boot. While I desire this for the data partition, I do not wish my 3 year old to have access to it. Can I just edit the line in a way to give me aceess in nautilus but not throuh the desktop?

UUID=10c2d27b-2b97-4aab-b03e-143b1323ba13	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda3 :
UUID=69A6C422493790CA	/media/Data	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda1 :
UUID=5A918A044377AE66	/media/sda1	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
#Entry for /dev/sda6 :
UUID=8a5fbed4-6f33-4e2a-b1d9-b4838d755bd4	none	swap	sw	0	0

P.S. I know if I had backed it up first I would have the line to replace already...oops!

---

### Post by Impavidus on 2014-04-21
You could add the **noauto** option. Then it won't automount. The only way to mount would be by giving the sudo password.
You could also add the **ro** (read only) option. Then damaging the Windows system becomes impossible. It's better to mount Windows C partitions read only anyway, as Windows doesn't like it when it's C partition is modified from the outside.

---

### Post by poliltimmy on 2014-04-21
So I substitute defaults with noauto? Then when I want to mount it will need a passwaord. Is this correct?

---

### Post by Impavidus on 2014-04-21
You can add the noauto option after the defaults option, as in```
defaults,noauto,locale=en_US.UTF-8
```It will require a password to mount. In the same way you can add the ro option, or both.

---

### Post by poliltimmy on 2014-04-21
All I really want to do is put it back to the defaults the install did. Be able to access but not auto mount it. Anyone got a default dual boot and can give me a copy of the fstab in theirs, everything after ntfs on the line?

---

### Post by steeldriver on 2014-04-21
The 'default' is not to have an entry for it at all in /etc/fstab - then it may be user-mounted from nautilus by clicking on the drive icon (which uses gvfs and doesn't refer to the fstab file). However there's nothing to stop your 3yo from doing that...

---

### Post by poliltimmy on 2014-04-21
She only uses desktop shortcuts. So, if I just delete it in fstab all will be as it was?

---

### Post by steeldriver on 2014-04-21
or just comment it out (put a # in front) in case you want to go back

---

### Post by poliltimmy on 2014-04-21
Commenting it out did the trick. Thanks a bunch.

---

