---
title: "I screwed with ubuntu and now i cant move the grub kernel"
date: 2008-02-16
forum: General Help
---

### Post by twoprophets on 2008-02-16
So my parents told me that i had to remove ubuntu from my computer and i really loved the OS, but my computer just couldnt handle it. My computer is an older model and was having trouble supporting both windows and ubuntu. So i searched on google and found a forum post telling how to remove all of ubuntu. i used that command and now every time i reboot my computer it comes up with black background and white lettering and that is it. i then discovered that i had to move the grub kernel or else i couldnt load my windows partition. So i googled and came up with a result from the ubuntu forums. The only thing that i didnt have was an ubuntu cd and the OS in correct operating fashion(as mentioned above). So i go in to try and see if it work without the cd and i login and put in grub. It goes to the grub part and then i put in find /boot/grub/stage1. I kept getting error 15. So i am in need of help.

---

### Post by aashay on 2008-02-16
Just pop in the windows xp cd and repair your previous installation. The command is fixboot (from the recovery console) as far as i can remember

---

### Post by pointone on 2008-02-16
The command is fdisk /mbr.

---

### Post by Ptero-4 on 2008-02-16
The command is fixmbr (fdisk /mbr is for win9x and winME).

---

