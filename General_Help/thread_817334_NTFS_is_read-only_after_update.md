---
title: "NTFS is read-only after update"
date: 2008-06-03
forum: General Help
---

### Post by tsphere on 2008-06-03
I did a mistake and enabled hardy-proposed source library.
Now my NTFS drive is suddenly read only.
Here is my fstab line for automounting:

```
/dev/sda1    /media/disk ntfs  nls=utf8,umask=0222 0    0
```

I don't know if I need to change the line, or if there is something I can do to reverse the update (I already deselected hardy-proposed), but it didn't roll back.

Thanks,
Eyal

---

### Post by peakshysteria on 2008-06-03
Enabling hardy-proposed didn't do antything to my two ntfs disks. They are still read and writable.

Do you still have ntfs-3g and ntfs-config installed? If not, install via synaptic. Make sure no disks are mounted. Then run ntfs-config from **applications --> system tools**

---

### Post by tsphere on 2008-06-04
Thanks for your reply. I hadn't installed ntfs-3g because hardy is supposed to support it by default.

And it did, out of the box. Only now it is suddenly read only.

---

### Post by frogitts on 2008-06-04
Same problem here - and it doesn't change even after unchecking "mount in read only mode" and remounting in System > Administration > Storage Device Manager.

EDIT: Mine works now after using the terminal from Ctrl+Alt+F1 and executing "sudo shutdown 0".

EDIT again: However, execution of files is prohibited by default now. After running "mount" in terminal, I get "rw,noexec,nosuid,nodev,noatime,allow_other,blksize=4096" as the attributes for my mounted drive. I specified "exec" in the options for the drive in Storage Device Manager.

---

### Post by peakshysteria on 2008-06-04
What about ntfs-config in synaptic? I installed both ntfs-3g and ntfs-config. None was there after a clean install of Hardy. No after both are enabled in synaptic all is well.

---

