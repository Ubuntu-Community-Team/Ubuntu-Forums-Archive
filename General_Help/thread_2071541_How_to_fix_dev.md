---
title: "How to fix /dev?"
date: 2012-10-15
forum: General Help
---

### Post by BURGINABC on 2012-10-15
This is really embarrassing, and I feel like an idiot, and I'm not even going to try to explain how this happened, but if you accidentally delete everything out of /dev, how do you fix it?

---

### Post by Cheesemill on 2012-10-15
You don't, none of the files in /dev actually exist, they just refer to resources that the kernel knows about.

The contents of /dev are enumerated every time you boot your machine.

---

### Post by BURGINABC on 2012-10-15
hmm... well, since I did this, It hasn't booted right. When I deleted the files from /dev, I panicked and copied the files from /dev in another distro. Since then it hasn't booted up properly.

You say the kernel creates the files automatically at boot-time, so I'll try deleting the copies. 

I'm not quite sure how the block device files work, but I do know that it hasn't worked right since I did this.

---

### Post by BURGINABC on 2012-10-15
Hmm... It seems maybe the real problem didn't have anything to do with /dev. Instead, I think I accidentally copied a kernel from another distro into /boot. I deleted it and reinstalled grub and now everything's fine.

---

