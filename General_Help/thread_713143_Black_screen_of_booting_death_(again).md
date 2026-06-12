---
title: "Black screen of booting death (again)"
date: 2008-03-02
forum: General Help
---

### Post by qewrtyuiop on 2008-03-02
First off, I know there are a hundred posts on this but none of them seem to apply.
My first experience with ubuntu as normal, it booted quickly, rivaling windows and ran smoothley but when i installed Kubuntu (as a new install, not just KDE) it would take about 2~3 min to boot but would work.  After a while it suddenly stopped booting (hanging on the infamous black screen).  I then reinstalled ubuntu (normal) and now it does the same thing, black screen of death.  If I push Ctrl+Alt+F1 I get a normal booting output but every time I try to boot It will just stall on some step (there are several but not completely random).  I've let it sit for over an hour but nothing happened.  I'm running Ubuntu 7.10 clean install dual-booted with windows on a Dell Inspiron 1501 with an ATI graphics card.  
If it's a video issue, why did it work the first time (also 7.10)?
Thanks

---

### Post by Hmarroqu on 2008-03-02
press esc when you get the grub, and then boot in safe mode or whatever...im sure it will show you what its getting stuck on

---

### Post by qewrtyuiop on 2008-03-02
You mean when you select the OS?  Nothing happens  Currently its stuck on ACPI Exception (battery-0216) but that might change in a couple minutes

---

### Post by iris-n on 2008-03-02
well, if it's acpi it's not a video issue.
Try passing the boot parameter acpi=off to the kernel.
In the grub menu, select your ubuntu entry, press e, and type acpi=off at the end of the line starting with kernel.

If it works do the same thing with the /boot/grub/menu.lst to make it permanent.

---

### Post by qewrtyuiop on 2008-03-02
Thanks, It works.  What exactly is ACPI?

---

### Post by qewrtyuiop on 2008-03-02
Also, is there some way to disable networking durring boot?  It is trying to connect but cannot gain an IP so it just stopped.

---

### Post by iris-n on 2008-03-02
Advanced Configuration and Power Management.
It is known for compatibility problems on some hardware.

I haven't quite understood what you want to do. You could always disable the network device on the BIOS, if you want to get rid of it.

---

