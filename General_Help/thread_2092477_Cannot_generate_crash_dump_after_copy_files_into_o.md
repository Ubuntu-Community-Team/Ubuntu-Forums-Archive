---
title: "Cannot generate crash dump after copy files into ocfs2 filesystem."
date: 2012-12-07
forum: General Help
---

### Post by legolin on 2012-12-07
Hi all:
   I recently days, we are running ocfs2 on our network block device driver. But I encounter 1 issue that when I copy files into ocfs2 filesystem, the linux will crash when copying files. This issue won't happens when I using ext3. For debug this issue, I have installed linux-crashdump and using echo c > /proc/sysrq-trigger. After reboot, I can see vmcore and using this file for debugging. I also embed BUG_ON(1) on my code, it also works for generate crash dump. But when I using ocfs2, ubuntu won't generate crash dump after reboot.

My environment: Ubuntu 12.04 LTS
OCFS2: 1.6.3-4ubuntu1

Can anyone provide clue for this issue?? (Why crash won't generate crash dump).

Thanks a lot

---

