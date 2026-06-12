---
title: "Help!"
date: 2007-04-18
forum: General Help
---

### Post by trents on 2007-04-18
Can somebody copy and post the syntax for the Windows Longhorn boot lines from the Edgy "/boot/grub/menu.lst file" ? I cut and pasted those lines in the wrong place and they were deleted by the kernel upgrade. Now i can't get into Windows.

Thanks, Steve

---

### Post by bwhite82 on 2007-04-18
Try putting this at the very bottom of the file:
> 
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

Do note that your Ubuntu kernel options will be directly above this text, if you're not sure what you're doing, post your menu.lst here.

---

### Post by trents on 2007-04-18
Thanks a million, Soldierboy !

---

