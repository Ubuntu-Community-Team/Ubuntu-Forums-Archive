---
title: "Libre Office Calc fails to highlight or border active (current) cell"
date: 2017-03-31
forum: General Help
---

### Post by interglossa on 2017-03-31
I am running Ubuntu 16.04 on an Acer 1410 and after a fresh install of Ubuntu 16.04 on a system which had previously been upgraded from the previous LTS, I find the active cells in Libre Office Calc are not surrounded by a border.  I am wondering if people have encountered this on other platforms.

---

### Post by vasa1 on 2017-03-31
Completely close LibreOffice and then try changing themes? Does that help?

Completely close LibreOffice and then temporarily rename *~/.config/libreoffice* to something else. It's possible your profile has been corrupted. Does that fix the problem when you run Calc now?

---

### Post by speartip on 2017-03-31
I had this problem in Kubuntu. But installing libreoffice-gtk3 solved it for me.
Worth a try.

---

### Post by vasa1 on 2017-03-31
> **speartip said:**
> I had this problem in Kubuntu. But installing libreoffice-gtk3 solved it for me.
Worth a try.

Definitely worth a try!

---

### Post by RosscoRossco on 2017-05-16
I had this problem in ubuntu MATE 16.04. But installing libreoffice-gtk3 solved it for me also.

---

