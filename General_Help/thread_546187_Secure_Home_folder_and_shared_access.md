---
title: "Secure Home folder and shared access"
date: 2007-09-08
forum: General Help
---

### Post by hrod beraht on 2007-09-08
I would like to secure my home folder (/home/me) so that it is unavailable to other users on the same machine. I figured a **chmod 700 /home/me** would do the trick.

However, I have a shared sub-folder (/home/me/shared) that is accessed via Samba by a Windows machine on my network. If I chmod 700 my home folder, it also denies access to the shared sub-folder.

Is there any way to secure my actual home folder from access while still allowing shared access to the sub-folder? Or, am I just going to have to move the shared folder somewhere besides my home folder?

Thanks for any info,
Bob

---

### Post by merlinus on 2007-09-08
Having a shared folder in your /home does not seem a wise choice, to me.

-merlin

---

