---
title: "I installed Hardy Heron using Wubi through vista, could i remove vista?"
date: 2008-05-10
forum: General Help
---

### Post by gottabeandrew on 2008-05-10
I installed Hardy Heron using Wubi through vista. Would it be possible to remove vista and still have ubuntu? If not, could i somehow save all of my preferences and set-up for ubuntu, uninstall vista then install ubuntu by itself with the same configurations?

---

### Post by pytheas22 on 2008-05-10
I think that you can take the image file on the NTFS system in which Ubuntu currently resides, wipe the hard disk, and then put the Ubuntu image back onto it.  I don't know exactly how to do that but I've read that it can be done.

Another option would be to copy the entirety of your current /home folder onto external media, install Ubuntu using the CD, and then replace the /home directory on the new install with the old one from your existing system.  This should preserve all of your personal settings (wallpaper, bookmarks, mail...).  System settings would be lost and you'd have to reinstall any software that doesn't come by default, although it may be possible to get around this by also copying your old /usr and /etc directories into the new system using the same approach as the one applied to /home.  But I can't guarantee that that would work.

---

