---
title: "VMware will not run"
date: 2005-06-22
forum: General Help
---

### Post by jallain on 2005-06-22
I have searched the forums without finding a solution to my problem. I installed the latest version of vmware on Hoary Hedgehog without any problems. It installed and configured just fine, all the modules load in the kernel with no problem. The problem is that vmware will just not run. This is the message I get:

  VMware Workstation Error:
VMware Workstation unrecoverable error: (vmui)
Unable to initialize host: Message
A log file is available in "/tmp/vmware-jeff/ui-8882.log".  Please request support and include the contents of the log file.
To collect files to submit to VMware support, run vm-support.
We will respond on the basis of your support entitlement.

Press "Enter" to continue...
Unable to initialize host: Message


Any ideas????

---

### Post by jallain on 2005-06-22
Please disregard this message. I waded through my own stupidity and discovered that my preferences file (copied from another partition) did not have the right permissions. Once I corrected that, vmware works just fine.

Jeff

---

