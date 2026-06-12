---
title: "I need help on uninstalling ubuntu(refuses to uninstall)"
date: 2008-06-12
forum: General Help
---

### Post by pmokgweetsi on 2008-06-12
Hallo guys can anyone help me...I recently installed ubuntu on my computer and after a go at it for a few days i decided to uninstall it cause it caused a whole lot of problems to my computer like frequent crashes...not being able to use some devices, no wireless internet etc etc..but now i have a problem in the sense that when i start my computer it appears as if ubuntu is still there coz the computer still gives me two choices of operating systems that is, windows vista and ubuntu though i've deleted ubuntu. How do i completely phase out any traces of ubuntu so that it does not even appear when i boot my computer cause im afraid if I or anyone else who uses my computer accidentally chooses ubuntu my computer automatically crashes...can anyone help me out?


Thank you.

---

### Post by danwood76 on 2008-06-12
YOu need to reinstall the microsoft MBR.
This can be done from within Ubuntu (off the cards obviously unless you have a Live/Install CD)
It can be done from a vista install CD/DVD by selecting fix boot when the options come up.
Can be fixed within the grub boot disk.

Do you have any of the above?

---

### Post by louieb on 2008-06-12
How did you install Ubuntu? Normal install on its own partition or wubi?

Answer is different for the two types of install.

---

### Post by pmokgweetsi on 2008-06-12
> **danwood76 said:**
> YOu need to reinstall the microsoft MBR.
This can be done from within Ubuntu (off the cards obviously unless you have a Live/Install CD)
It can be done from a vista install CD/DVD by selecting fix boot when the options come up.
Can be fixed within the grub boot disk.

Do you have any of the above?

No I don't have any of those coz my computer came already complete with windows installed. I didn't buy the installation CD. So how do i fix it? If it will be helpful, when i installed ubuntu i installed it inside windows, not as a separate independent operating system.

Thanks.

---

### Post by louieb on 2008-06-12
Did you use the add-remove program feature in windows to uninstall?  

May just want to live with it.  Windows uses a hidden file **c:\boot.ini.  **Probably can  use a text editor to edit and remove the Ubuntu entry from it.
 
Be sure to create a backup of the file before making any changes.

---

### Post by meierfra. on 2008-06-13
[How to edit boot.ini]("http://support.microsoft.com/kb/289022")

---

### Post by danwood76 on 2008-06-13
I recomend the super grub disk.
Its only a 4MB download, you will have to burn the iso to a CD using something like DVD decrypter (the free option) or nero or whatever.

Get the SGD (super grub disk) here:
[http://www.supergrubdisk.org](http://www.supergrubdisk.org)

Here is a guide to uninstalloing grub:
[http://www.supergrubdisk.org/wiki/UninstallGRUB](http://www.supergrubdisk.org/wiki/UninstallGRUB)

---

