---
title: "Does Virtualbox affect GRUB?"
date: 2008-06-09
forum: General Help
---

### Post by nerd0795 on 2008-06-09
I tried asking this on the virtualbox forums and they said read the manual.  I read it and you know what it doesn't say it.  So I'm going to ask this here.

I have a dual boot with Vista and Ubuntu.  I want to run Windows ME under ubuntu to on purposely damage windows me so I can practice fixing it.  Now the thing is does having a virtual pc affect GRUB?!  I really need to know.  Does it add another OS to the list?

I am using Ubuntu 8.04

---

### Post by bollix47 on 2008-06-09
Nope, installing VB makes no changes to GRUB.

[VirtualBox HowTo]("http://ubuntuforums.org/showthread.php?t=770745")

---

### Post by bingoUV on 2008-06-09
It is not designed to affect your grub entries at all. It just boots up a fake computer. The OS running inside your fake computer cannot affect anything inside your real OS. This one of the guiding principles of virtualization.

In general, if you do not run a program as root, it just cannot affect your grub entries. Or change anything system wide. Since you will run virtualbox as a non-root user, even if there is a severe defect in virtualbox it cannot do anything to your grub entries.

---

### Post by inportb on 2008-06-09
Let's put it this way... Virtualbox does not affect the host GRUB. You can most certainly affect the virtualized GRUB, however.

---

### Post by dicecca112 on 2008-06-09
> **inportb said:**
> Let's put it this way... Virtualbox does not affect the host GRUB. You can most certainly affect the virtualized GRUB, however.

VirtualBox is a program, it does nothing to GRUB in the same way Pidgin or any other program in Ubuntu

---

