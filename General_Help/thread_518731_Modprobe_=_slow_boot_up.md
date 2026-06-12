---
title: "Modprobe = slow boot up"
date: 2007-08-06
forum: General Help
---

### Post by aimran on 2007-08-06
HI guys!

I have been consistently having 2 minute hangs on boot up. Installing bootchart shows that modprobe uses about 150 seconds during boot up.

Anyone got a solution to this?

---

### Post by nick_h on 2007-08-07
The output of *dmesg* might show where the problem is.

---

### Post by psusi on 2007-08-07
modprobe loads drivers, so it sounds like one your system is loading has some problems.

---

### Post by aimran on 2007-08-08
Thanks for the replies. Dmseg output is too long to post here. But thanks for pointing me in the right direction.

---

