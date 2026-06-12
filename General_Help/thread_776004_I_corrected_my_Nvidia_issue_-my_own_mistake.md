---
title: "I corrected my Nvidia issue -my own mistake"
date: 2008-04-30
forum: General Help
---

### Post by billrad1 on 2008-04-30
I did the upgrade online, and after reboot, my Nvidia drivers would not work. I went round and round on this for a day.

I finally realized what I had done wrong. Maybe it will help you.

When I was prompted to keep or update Menu.lst during the install, I said keep it. I had a customized entry to dual boot windows.

Well, I forgot about it, and so at every reboot, I was booting the old kernel.  Duh

I edited Menu.lst and added the new kernel option, then rebooted, jumped out to the command line as root, stopped GDM, installed the Nvidia driver from the Nvidia site. 

It worked like a charm. Back in business. Hope this helps.

br

---

