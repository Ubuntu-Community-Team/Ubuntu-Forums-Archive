---
title: "&quot;superblock&quot; message after deleting partition"
date: 2007-04-06
forum: General Help
---

### Post by JAPrufrock on 2007-04-06
I used gparted while working in Gnome to delete a ext2 partition that I had never used.  The partition was deleted OK, but I get the following message whenever I boot up: "The superblock could not be read or does not describe a correct ext2 filesystem.  etc. etc."  Once I do boot up, however, everything seems to be fine.  So I guess my question is anyone know how to remove the message??

---

### Post by cisforcojo on 2007-04-06
So when you bootup, it displays this error but still boots? That's odd. I've had this error before but it wouldn't load.

The discrepancy is between your actual partition tables and what GRUB believes them to be. 

You could try re-writing GRUB to your MBR.  This might fix the problem.

---

### Post by JAPrufrock on 2007-04-06
> **cisforcojo said:**
> So when you bootup, it displays this error but still boots? That's odd. I've had this error before but it wouldn't load.

The discrepancy is between your actual partition tables and what GRUB believes them to be. 

You could try re-writing GRUB to your MBR.  This might fix the problem.


When it stops loading and gives me the error message, I press return and then type "exit" and it then continues to load.  

I tried re-writing Grub to MBR, using grub-install, but I get the same error message.  I may have to live with it.

---

