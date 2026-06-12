---
title: "Auto-decrypt drives on login"
date: 2012-10-22
forum: General Help
---

### Post by M@s on 2012-10-22
I've encrypted my storage drives with excryptfs using the Disk manager with success. But to actually decrypt them and make them accessible I have to open up Nautilus and click on them to make them mount.

How can I get this done automatically on boot? As I understand they're already mounted, but not the encrypted layer...


Ubuntu 12.04 (dream studio)

---

### Post by doktorOblivion on 2012-10-22
I encrypted my entire drive using the alternate CD and in so doing I have the following in my /etc/init.d directory which appears to perform this function, do you?

```

-rwxr-xr-x   1 root     root       922 Mär  8  2012 cryptdisks
-rwxr-xr-x   1 root     root       871 Mär  8  2012 cryptdisks-early
lrwxrwxrwx   1 root     root        21 Apr 14  2012 cryptdisks-enable -> /lib/init/upstart-job
lrwxrwxrwx   1 root     root        21 Apr 14  2012 cryptdisks-udev -> /lib/init/upstart-job

```

Hope this helps...

---

### Post by M@s on 2012-10-22
Yes, they're all there.

---

### Post by doktorOblivion on 2012-10-22
Not sure how much further I can help since I am using logical volume support with LUKS.  Have you considered that?  Or do you only want a certain part of you f/s protected?  Guess it depends on what you were initially thinking.  If you want to go the install route, let me know, I have readme on that...

---

