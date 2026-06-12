---
title: "su and localhost problems"
date: 2006-12-04
forum: General Help
---

### Post by dnablen on 2006-12-04
i rebooted  my computer and the system panel says "su failed" and when i konsole login it says "dan@(none)". What do i do? btw im using the most recent kubuntu and kde.
-dan

---

### Post by rbil49 on 2006-12-04
Fix your /etc/hosts file.

Cheers.

---

### Post by dnablen on 2006-12-04
i tried that but i dont have access it says
any other suggestions?
-dan

---

### Post by taurus on 2006-12-04
Boot into recovery mode from the GRUB menu and edit /etc/hosts (and probably /etc/hostname).  Otherwise, you can boot with the LiveCD, mount your harddrive where / is located, and edit /etc/hosts on your harddrive.

---

