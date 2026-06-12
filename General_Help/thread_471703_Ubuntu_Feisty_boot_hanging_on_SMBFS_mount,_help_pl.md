---
title: "Ubuntu Feisty boot hanging on SMBFS mount, help please?"
date: 2007-06-12
forum: General Help
---

### Post by malibu on 2007-06-12
I placed an smbfs automount in my /etc/fstab and now my boot is hanging.  Apparently Dapper had a bug that hangs on smbfs automount and I guess it hasn't been fixed for Feisty.  Now I need to get into my system!  How do I get around the hang?  I tried selecting the 'recovery mode boot' in the grub menu but it still wants to mount the smbfs filesystem and also hangs.

How do I boot at this point with only the root filesystem mounted?  Thanks!

---

### Post by bscbrit on 2007-06-12
Use your live CD.  When running in live CD mode, edit fstab to remove the offending line.  Save the file, and then reboot as normal.

---

