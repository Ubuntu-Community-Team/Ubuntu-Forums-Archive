---
title: "Kernel sync panic"
date: 2007-11-30
forum: General Help
---

### Post by polypill on 2007-11-30
I have an Ubuntu gutsy LAMP server using a software raid 1 and it had been running for about a month without issue and 2 days ago out of no where the system crashed (hang, no response from anything) and I couldn't find any error messages in any logs. I rebooted it and yesterday morning it crashed again without explanation, so I rebooted and left the monitor displaying the terminal instead of the gdm gui. This morning it crashed again and spit out the error "kernel sync panic." Since I can't find anything in any logs, its just a gap of time from when the sever crashes, that's all I have to go by and I have no clue what that means. It is using kernel 2.6.22-14-server.

Can someone point me in the right direction or give me some ideas of what to check? I'm suspecting hardware but I'm not sure.

---

### Post by polypill on 2007-11-30
Anyone at all?

---

### Post by fjgaude on 2007-11-30
I would suspect RAM, memory. Without anything to go on in the logs, it could be the CPU... these are tough... good luck in finding the problem.

---

### Post by beaux on 2008-02-26
...I too have that happen to me... a while back I remember reading about the kernal being unaable to find the initrd file.  Deleting the initrd file is a subtle way that crackers prevent you system from re-booting. The initrd file is usually found in the "/boot" directory.

---

