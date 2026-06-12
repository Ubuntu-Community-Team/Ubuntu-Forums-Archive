---
title: "VMWare does nothing"
date: 2006-11-29
forum: General Help
---

### Post by LucidTaZ on 2006-11-29
Hey all,

I just installed VMWare Server following the routine described by VMWare. Now when I try running 'vmware' or 'sudo vmware' from a console, nothing happens. It doesn't return to the command line, nor does it show any windows or other state of activity.

Could someone help me out on this or give me advice please?

I'm running Ubuntu 6.10 Edgy Eft on an Acer Aspire 3616 laptop.

Thanks! :)

---

### Post by Paul41 on 2006-11-29
I recently installed VMWare with these instructions with no problems.
[http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+windows](http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+windows)

---

### Post by LucidTaZ on 2006-11-29
Yep. Tried it already without success. Thanks though. :)

---

### Post by KnevetS on 2006-11-29
I had that problem briefly, and it was due to the fact that I had booted with my iPod connected, which caused some general wierdness.  I rebooted after disconnecting the ipod and everything worked fine.

---

### Post by LucidTaZ on 2006-11-29
Thank you for your answer. I only have one device connected to my computer and that's my USB mouse. So I don't think that's the problem.

Any more suggestions? :(

---

### Post by LucidTaZ on 2006-11-29
Problem solved. I had both libdbus-1-2 and libdbus-1-3 installed. After removing libdbus-1-2, it suddenly could startup. :)

---

### Post by Tourmaline on 2007-01-14
Thanks to LucidTaz, removing libdbus-1-2 was the good solution too on my laptop with Kubunt 6.10and VMWare 1.01.

---

