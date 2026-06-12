---
title: "can't back up files with LiveCD boot"
date: 2008-05-18
forum: General Help
---

### Post by dwkreutzer on 2008-05-18
After a recent update, I am unable to boot up. I get error messages about not being able to mount various things.

"Target file system doesn't have /sbin/init" is the last of these messages.

My proposed solution is to go ahead and upgrade to 8.04.  Before doing that, I wanted to back up my files.

So, I boot up with an 8.04 LiveCD.  It goes fine.  I can open all the files (almost).  But I can't copy anything to my external hard drive.

The external hard drive is recognized, but when I try to copy files to it, a message pops up saying I don't have read permission.

So (at last) the question is: How can I get read permission when booting up via LiveCD?

Thanks for any help

---

### Post by wpshooter on 2008-05-18
Are you using the SUDO command ?

---

### Post by dwkreutzer on 2008-05-18
No.  I was just trying to drad and drop.

---

### Post by roe_polak on 2008-05-18
You need root privileges to write to drives when you're using a live cd. Start nautilus by using sudo, then you can write to the drives. Just be careful not messing up important data. Root privileges should give you access to all files.

---

