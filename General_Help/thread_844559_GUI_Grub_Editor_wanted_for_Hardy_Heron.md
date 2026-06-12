---
title: "GUI Grub Editor wanted for Hardy Heron"
date: 2008-06-29
forum: General Help
---

### Post by tobodestroyer on 2008-06-29
Hi,

I want to edit my Grub loader so that WinXp is still the default OS. Is there a nice GUI interface that will allow me to do this?

Tobo

---

### Post by manfer on 2008-06-29
You have to install the starup manager. Look for it in synaptic or from a terminal:

prompt:~$ **sudo apt-get install startupmanager**

Then you would find it in System->Admin

---

### Post by drs305 on 2008-06-29
I wrote some information about StartUp-Manager. It is a much safer way to edit options in the grub menu than manually editing menu.lst .

[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by tobodestroyer on 2008-06-29
Manfer,

Thanks for your swift reply. I've installed StartupManager and it works brilliantly.  
Many thanks.

Tobo

---

### Post by oldos2er on 2008-06-29
Just FYI, there's also Qgrubeditor.

---

