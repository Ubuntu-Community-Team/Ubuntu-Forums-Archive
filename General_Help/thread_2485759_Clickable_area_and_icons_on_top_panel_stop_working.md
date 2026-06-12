---
title: "Clickable area and icons on top panel stop working after suspend or lid close"
date: 2023-04-08
forum: General Help
---

### Post by Gordonbp531 on 2023-04-08
Ubuntu 22.04.2 LTS fully upgraded.
The icons and clickable area of the top panel do nothing until the machine is restarted - then after the first "suspend" it all stops working again.
I don't need or want to restart my machine every time the panel stops working.....
Any solutions?

---

### Post by MAFoElffen on 2023-04-08
Please post the output of this within CODE tags:
```

echo $XDG_SESSION_TYPE
grep . /sys/module/*_idle/parameters/max_cstate

```

---

### Post by Gordonbp531 on 2023-04-11
```
x11
9
```

---

### Post by MAFoElffen on 2023-04-11
Am I assuming correctly if I guess this CPU is Intel?

If so then try adding "intel_idle.max_cstate=4" to the "GRUB_CMDLINE_LINUX_DEFAULT=" line in '/etc/default/grub" file. The do
```

sudo update-grub

```

---

### Post by Gordonbp531 on 2023-04-11
Seems that's done the trick!
Many thanks.....

---

### Post by MAFoElffen on 2023-04-12
Glad it helped. Remember to use the thread tools link in the upper right of the page to mark it as solved so that other can find what worked for you.

---

