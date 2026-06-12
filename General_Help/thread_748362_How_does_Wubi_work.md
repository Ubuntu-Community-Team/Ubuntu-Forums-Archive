---
title: "How does Wubi work?"
date: 2008-04-07
forum: General Help
---

### Post by smartboyathome on 2008-04-07
I am creating a MultiBuntu DVD (almost done), and would like to know where I can get the sources for Wubi and how it works. I would like to include it on the DVD (origionally made using the Hardy Beta CDs), but allow the user to choose which version (Ubuntu, Kubuntu, or Xubuntu) to install. Would this be possible?

Thanks,
Smartboy :KS

---

### Post by ago on 2008-04-07
Not with the current code base, because your case would involve extracting a file from within the DVD while current code base extracts the whole DVD as an ISO (which would be wasteful), as well as the kernel/initrd. Code is in launchpad.net/wubi (hardy branch). If you see in the last section of the WubiGuide it talks about customization. It is of course possible to change the code to accomodate for DVDs, and I can have a look at it, but that will not be done before the final release.

---

### Post by smartboyathome on 2008-04-07
Ok, thanks for the info! I wasn't expecting it to be done as a final release, I was just wondering if it would be possible. :)

---

### Post by ago on 2008-04-07
You might be interested in [https://bugs.launchpad.net/wubi/+bug/201046](https://bugs.launchpad.net/wubi/+bug/201046)
The "won't fix" is for the 8.04 deadline.

---

