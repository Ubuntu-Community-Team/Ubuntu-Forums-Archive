---
title: "Wubi boot menu problems"
date: 2008-06-14
forum: General Help
---

### Post by TehDuke on 2008-06-14
I installed wubi with ubuntu 8.04, and when i chose to uninstall wubi, it didnt change the boot menu, so when i turn my computer on, i still have to select vista from the menu. (Selecting Ubuntu from the list doesn't work).

Ive tried editing the boot menu in VistaBootPRO and msconfig, but neither of them see Ubuntu and so i cant delete it from the list.

Thanks in advance for any help.

---

### Post by mimada on 2008-06-14
Did you try deleting the "ubuntu" folder in your "Program Files" (or wherever you installed it) directory? There may also be a couple of Wubi files on your C: drive: wubidr and/or wubidr.mbr.

I haven't tested the effects of deleting this stuff so you might want to rename them just to play it safe.

---

### Post by TehDuke on 2008-06-14
ive tried that, but it hasnt changed the boot menu.
thanks anyway though.

---

### Post by meierfra. on 2008-06-15
Try Easybcd (see my signature)

---

### Post by TehDuke on 2008-06-16
awsome, thanks meierfra, that EasyBCD program worked a treat.

---

