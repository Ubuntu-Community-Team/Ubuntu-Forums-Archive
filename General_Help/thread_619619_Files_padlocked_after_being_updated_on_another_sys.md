---
title: "Files padlocked after being updated on another system?"
date: 2007-11-21
forum: General Help
---

### Post by blop on 2007-11-21
Hi guys....i think i have made a boo boo.

I am sharing a folder through samba and ran this command thinking it would sort out permissions:

sudo chmod 0777 /home/matt/netshare

now...it kind of works....i can share files and other pcs can write to it. But i notice after copying a folder and a file to the shared folder from an XP machine.....the file and folder have little padlocks on them andi cant edit them.....


whats happened? does the XP machine own them?

---

### Post by rmemm on 2007-11-21
I don't use samba so can't comment specfically about samba.

However generally access in Linux is based on user and group ownership, and on the permissions bits.  You can see the file info with "ls -l" which will show both of these.

During creation a file's permissions and ownership are typically unrelated to the directory they are within.  Instead, they relate to who created the file or folder -- meaning their user name and group membership, and the permissions are related to the umask setting of that process.  Presumablly samba makes some choice here.

One way you can modify this behavior is to set the sgid bit on the folder, and in this case the group ownership of anything created in the folder will be switched to the group ownership of the folder.

This is one reason that generally on Linux people use separate group structure and a umask of 007 or 027 -- which creates files like rw-rw---- or rw-r-----. By this I mean, these sorts of umasks work well with shares depending on what you want.

Rob

---

### Post by blop on 2007-11-22
mmm...something to chew on.

thanks..

i will check out user permissions...cheerS!

---

### Post by u-slayer on 2007-11-22
You're files proably don't belong to you.

chown username:username files.

---

