---
title: "USB MP3 Player permissions."
date: 2006-11-10
forum: General Help
---

### Post by forcesofhabit on 2006-11-10
I know there are a lot of threads related to this type of thing, but perhaps this might be a little different?

I right click on the permissions and it says the owner has read & write permissions (owner being 'nolan') and then it says nolan has no permissions as does other.

I'm confused. I AM logged in, and I AM the owner. So why is everything write protected? How can I fix this?

Another odd thing, the first time I put files on the player, it worked no problems at all. Now when I plug it in, it has the problem stated above.

---

### Post by forcesofhabit on 2006-11-10
Anybody? :confused:

---

### Post by taurus on 2006-11-10
Is it fat32 filesystem?  I bet you it's mounted as read/write for root and read only for anybody else...  So if you want to write to it, you can use the sudo command or mount it by hand with read/write permission for user, nolan.

---

### Post by forcesofhabit on 2006-11-10
That didn't seem to have any effect on the device.
I still can't write to it, even when I am running as root.

It says root (root) can read and write
and right under that root can only read.

---

