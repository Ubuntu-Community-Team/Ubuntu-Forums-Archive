---
title: "Kubuntu Had It"
date: 2006-12-10
forum: General Help
---

### Post by wireddad on 2006-12-10
When I'd tried Kubuntu, noticed that under printers there was an option to print to pdf printer already loaded.  I am now using Edgy.  Can anyone tell what the pdf program in Kubuntu so I can possibly install it in Edgy?  Or is it in the Add/Removew Program and I just do not know the name.  Thanks.:-?

---

### Post by meng on 2006-12-10
I think it's cups-pdf.

---

### Post by wireddad on 2006-12-10
I will check.  Thanks.

---

### Post by meng on 2006-12-10
You may be better off using Adept, or else the command line (aptitude) rather than Add/Remove Programs.

---

### Post by wireddad on 2006-12-10
Sorry but have not had the opportunity to check in Add/Remove.  So Meng, you are saying I should install Adept and attempt to install cups-pdf?

---

### Post by meng on 2006-12-10
By far the easiest way is to drop to the command line and:
sudo aptitude install cups-pdf

BUT you must have universe repositories enabled! Search the wiki if you don't know how.

---

