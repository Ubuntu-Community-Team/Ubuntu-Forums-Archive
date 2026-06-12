---
title: "delete stuff from external drive"
date: 2007-04-17
forum: General Help
---

### Post by Bobtheknight on 2007-04-17
My betters,

I am trying to delete stuff from my external drive.  So I press delete, they end up in my desktop trash.  But when I go "empty trash" trash tells me "/media/disk...rtSmall.jpg" cannot be deleted because you do not have permissions to modify its parent folder."

I am going to use rm from command line now, but is there a way to rig the GUI such that I can use "empty trash" button?

Bob

---

### Post by HumanAnarchist on 2007-04-17
It could be a bug in nautilus, but if you go to Nautilus -> Edit -> Pref -> Behavior and check the field "include a Delete command that bypasses Trash" it could work...

-ha-

---

### Post by Bobtheknight on 2007-04-17
Thanks for the suggestion,  I hope it works :D

---

### Post by HumanAnarchist on 2007-04-17
Did it work?

---

### Post by HiSPEC on 2007-04-17
I think that the problem was, that you mounted it as root, and therefore you can't delete information from it.
Try deleting information as root, make it user-mountable via /etc/fstab, or mount it with uid=UID,gid=GID.

---

### Post by Bobtheknight on 2007-04-17
Edit:  It seems to work for now, thanks a lot!

HiSPEC, the thing automounts, how do I findout if it mounts as root?

---

### Post by HiSPEC on 2007-04-18
> **Bobtheknight said:**
> Edit:  It seems to work for now, thanks a lot!

HiSPEC, the thing automounts, how do I findout if it mounts as root?

what automounts? /etc/fstab ?
well, it mounts as root unless you say uid=X,gid=X.

---

### Post by Bobtheknight on 2007-04-18
Em, the external harddrive automounts.  How do I do uid = X, gid = X?
Can I have a step by step instruction if it's not too much trouble?  ;P

---

### Post by strabes on 2007-04-18
When you want to permanently delete things, you can use shift+delete I think. This works in konqueror, don't know about nautilus.

---

