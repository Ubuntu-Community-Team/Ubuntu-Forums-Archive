---
title: "Ubuntu 18.04.2 unresponsive on hd activity"
date: 2019-02-18
forum: General Help
---

### Post by nibbli on 2019-02-18
When stuff is written to hd, my Ubuntu 18.04.2 gets kind of unresponsive.

To reproduce:
echo /dev/zero > test

Then click the Google Chrome icon (or anything else) on the left and see how nothing happens until CTRL+C on aforementioned command. The disk is a mini PCI SSD. Changing the scheduler on the disk to noop doesn't help. It is a laptop Dell Precision M4600 with chipset Mobile Intel QM67 Express. Is there a solution to this?

---

### Post by nibbli on 2019-02-19
Does anyone have the same issue? Is it a known bug? I searched the forum for "unresponsive", but couldn't find anything. This also happens with regular disk activity, not only with this artificial test.

---

