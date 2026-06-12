---
title: "File copy hangs"
date: 2024-05-13
forum: General Help
---

### Post by a-daniel-8 on 2024-05-13
I have the same problem and it started about a month ago. It's intermittent but very annoying since it totally interrupts my workflow.

It occurs seemingly random when I try to copy a file on a CIFS mount. I've tried switching from nautilus but it still occurs so it's seem to be an underlaying problem.
The only way around it I've found is to restart the computer. Logging out doesn't really do it and unmounting is not possible since the file system is busy.

My co-workers mostly run windows and use the same share but they have no problems with it.

Ubuntu 22.04.4 LTS and kernel 6.5-28.

---

### Post by a-daniel-8 on 2024-05-13
I actually have to reboot the computer to get out of the deadlock. When I reboot nautilius is hanged so it won't reboot and power cut is the only way out.
I've now changed to sshfs (instead of cifs) to see if that works better.

---

### Post by coffeecat on 2024-05-13
Posts split into their own thread from [https://ubuntuforums.org/showthread.php?t=2491880](https://ubuntuforums.org/showthread.php?t=2491880)

---

