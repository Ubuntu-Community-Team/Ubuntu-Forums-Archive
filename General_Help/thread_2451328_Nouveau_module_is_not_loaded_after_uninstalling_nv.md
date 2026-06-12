---
title: "Nouveau module is not loaded after uninstalling nvidia driver"
date: 2020-10-01
forum: General Help
---

### Post by Magnusmaster on 2020-10-01
I uninstalled the nvidia driver through the GUI since it caused crashes and hangs... but after restarting the nouveau module does not get loaded. ```
lsmod | grep nouveau
``` shows nothing. Any help?

---

### Post by guiverc on 2020-10-01
I would check it's not blacklisted (thus your system has been told not to use it; which can occur by nvidia scripts I believe, to ensure the nvidia module is used).

Look in /etc/modprobe/d/blacklist.conf

---

### Post by Magnusmaster on 2020-10-02
Turns out there was a file /etc/modprobe.d/nvidia-340_hybrid.conf that blacklisted nouveau that for some reason was not deleted. After deleting it nouveau works

---

### Post by TheFu on 2020-10-02
Please use "Thread Tools" button to mark this thread as solved.

---

