---
title: "Bad kernel update and no net"
date: 2006-09-15
forum: General Help
---

### Post by ÄlveKatt on 2006-09-15
What the topic says. I did the bad kernel update, things stopped working. But when I tried to do the fix described here; [http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459) it failed to connect.

I figured I am the victim of the bug described here; [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/60271](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/60271)

I have an Asus a6Jm laptop. 

So, how do I go about fixing this without a net connection? I am quite desperate. I need access to my school work, among other things...

---

### Post by PriceChild on 2006-09-15
Have you tried reverting back to an old kernel from grub, or installing from your cache located at /var/cache/apt/archives

This could temporarily solve the problem, allowing you to ensure you fully complete the fix described above before rebooting into the new kernel.

Pricey

---

