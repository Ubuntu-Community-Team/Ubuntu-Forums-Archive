---
title: "external drive and permissions"
date: 2020-12-14
forum: General Help
---

### Post by crackers_altitude on 2020-12-14
I formatted an external SSD as ext4, using the rescue DVD as it turns out. I did not pay to much attention to the permissions as I assumed it would be correct.

As the main Ubuntu installation is up and running now, I went to mount the drive. The encryption (LUKS) appears to have worked, however, the permissions are "systemd-coredump", and I only know that because I have to `sudo` to even `ls` anything. Writing is - apparently - impossible even with `sudo`.

I suppose I am looking for how to change permissions, how to set permissions during formatting, or something else?

---

### Post by ajgreeny on 2020-12-14
Formatting the disk , or rather the partition on the disk, as ext4 will mean that by default it is owned by root.

I assume that it is mounted automatically when attached to the system, meaning it will mount at /media/username/UUID or if the partition is labelled, which I would highly recommend, at /media/username/Label.

Whatever the mountpoint is when attached you need to change ownership of that to you as user with command ```
sudo chown -R username:username /media/username/Label
```
The disk should now automount as read/write for you as user.

---

### Post by crackers_altitude on 2020-12-14
Woo hoo! works perfectly!... (so far ;^) ) thank you!

---

