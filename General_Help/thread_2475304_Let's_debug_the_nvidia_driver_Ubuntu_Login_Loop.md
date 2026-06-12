---
title: "Let's debug the nvidia driver Ubuntu Login Loop"
date: 2022-05-21
forum: General Help
---

### Post by hrsetrdr on 2022-05-21
Never  had this occur until recent times, now it's happened on 3 different machines. Google search shows that the "Ubuntu Login Loop" associated with a recent Nvidia driver installation is happening in significant numbers.  Further search leads to a simple procedure to correct the problem.

So, what *is* the problem?  Some component of the Linux kernel? The Nvidia drivers? Or...?

---

### Post by hrsetrdr on 2022-05-21
I found a post on[ reddit ]("https://www.reddit.com/r/archlinux/comments/s3vvzc/mate_login_loop_with_nvidia_proprietary_drivers/")where an Arch-Linux user made the statement that the "bug" was associated with  Mate's compositor marco and a new version of the nvidia driver.  he referred to a bug report someone filed: [https://bugs.archlinux.org/task/73031](https://bugs.archlinux.org/task/73031)

This is significant to me, being a Mate DE user.  I'm going to do some testing, adding XFCE to one of the machines and then doing an Nvidia proprietary driver install.

---

