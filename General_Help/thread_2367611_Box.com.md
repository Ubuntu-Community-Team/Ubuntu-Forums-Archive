---
title: "Box.com"
date: 2017-08-01
forum: General Help
---

### Post by Donnut on 2017-08-01
Hi all, I'm having trouble connecting to box.com with WebDAV. I'm following this guide([http://xmodulo.com/how-to-mount-box-com-cloud-storage-on-linux.html](http://xmodulo.com/how-to-mount-box-com-cloud-storage-on-linux.html)), but I can't mount it, it says ```
stephen@stephens-MacBook:~$ mount Box.com
/sbin/mount.davfs: user stephen must be member of group davfs2

```
I've already added myself to the user group, I even checked in gnome user tools to ensure I was in the group, which I am. What could I be doing wrong?

---

### Post by Donnut on 2017-08-02
Nevermind, It works now. Apparently you need to restart your system after a user  change, not just log out and in.

---

### Post by 1clue on 2017-08-02
User changes require logout and login again, but sometimes they need a complete logout. Meaning all connections with that account to that box. If you had a text terminal login, or an ssh session, or something like that some features might not reset. Most of the time though if you simply initiate a new session after a user/group change the change takes effect for that connection while not being in effect for the other pre-existing connections.

---

