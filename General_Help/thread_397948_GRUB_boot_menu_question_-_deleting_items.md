---
title: "GRUB boot menu question - deleting items"
date: 2007-03-31
forum: General Help
---

### Post by AlexBryan on 2007-03-31
Hi, this will probably a simple yes or no answer.
I have a bunch of options on my GRUB boot list, like previous versions of ubuntu of something. There are about 6 options for Ubuntu and one for Windows at the end. I know how to edit the boot list, so can I just delete the items I don't want from the list and leave the first ubuntu and the windows options, or will that bugger everything up?

---

### Post by taurus on 2007-03-31
Yes, you can delete the entries for the old kernels or just place a # in front of them to comment them out.

---

### Post by ajgreeny on 2007-03-31
If the entries are still there it also means all the old kernels are still installed.  You might want to uninstall them with apt or synaptic as well.  In fact if you do that, the menu.lst file will be updated automatically.

---

