---
title: "installing ubuntu on pointsec encrypted drive using wubi"
date: 2008-03-01
forum: General Help
---

### Post by krychek on 2008-03-01
Hi!
My company laptop has a pointsec encrypted hdd and we're not allowed to make any other partition. So I had no chance to have a dual boot system but now there's wubi. It doesn't need a new partition, but I'm still not sure if it's gonna work or not. Pointsec is the first thing that starts when i turn on the machine if it's booted from the hdd. If I use an ubuntu live cd then pointsec won't start. Question is what will happen if I install Ubuntu from windows 2000 using wubi? Will pointsec start first and then I can choose between windows and ubuntu? I hope it won't screw up anything..

Thanks

---

### Post by ago on 2008-03-01
Probably it won't work but I guess you can try it and in case uninstall.

---

### Post by krychek on 2008-03-01
Why won't it work? Will windows work at least?

---

### Post by ago on 2008-03-01
It depends on how the decryption works, in any case you can install and uninstall with affecting windows.

---

### Post by ago on 2008-03-01
It depends on how the decryption works, in any case you can install and uninstall without affecting windows.

---

### Post by krychek on 2008-03-01
Ok, I've tried it. The installation goes fine, pointsec starts first when i boot. After it asks if I wanna start win or ubuntu. Windows works fine, however ubuntu is just loading and loading and the HDD makes really strange noises. Too bad I can't see any output cuz there's only the splash screen while it's loading. Is there I way to see the actual output that might help something? I've tried hitting escape that does nothing.

---

### Post by ago on 2008-03-01
Use Wubi rev 443+, press esc after selecting "Ubuntu", then select verbose mode.

---

### Post by krychek on 2008-03-03
It doesn't really say anything useful. Only the hdd gives noises like it's gonna crash. Maybe I should have waited longer.

Here is a bug about this that someone else reported:
[https://bugs.launchpad.net/wubi/+bug/119607](https://bugs.launchpad.net/wubi/+bug/119607)

I don't know if this "bug" can be fixed..

---

### Post by amlucent23 on 2008-03-21
> **krychek said:**
> It doesn't really say anything useful. Only the hdd gives noises like it's gonna crash. Maybe I should have waited longer.

Here is a bug about this that someone else reported:
[https://bugs.launchpad.net/wubi/+bug/119607](https://bugs.launchpad.net/wubi/+bug/119607)

I don't know if this "bug" can be fixed..


I can confirm with the OP. Ubuntu installed through Wubi does not work on pointsec encrypted drives.

---

### Post by Unixus on 2010-05-03
Has there been any progress on this since 2008? :?:

---

