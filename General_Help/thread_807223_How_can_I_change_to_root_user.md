---
title: "How can I change to root user?"
date: 2008-05-25
forum: General Help
---

### Post by asintu on 2008-05-25
Trying to install an nvidia driver package but says I have to run it as root. How?

---

### Post by bwhite82 on 2008-05-25
use **sudo** in front of the command. Sudo gives you temporary root privileges. You'll need to supply your password after you type the command.

---

### Post by ibuclaw on 2008-05-25
**Direct Answer:**
To change to root, use:
```
sudo -s
```

**NVIDIA Drivers:**
Go into "**System>Administration>Hardware Drivers**" and enable the NVIDIA card there.
It's much simpler...

Regards
Iain

---

### Post by asintu on 2008-05-25
> **tinivole said:**
> **Direct Answer:**
To change to root, use:
```
sudo -s
```

**NVIDIA Drivers:**
Go into "**System>Administration>Hardware Drivers**" and enable the NVIDIA card there.
It's much simpler...

Regards
Iain

ya, I did that but I dunno my video card fan is working at full speed making lots of noise. And I dunno how to access the speed control.

So I'm trying to install the whole package 64-169 package from the nvidia site and hope I can change the speed of the fan that way.

---

### Post by ibuclaw on 2008-05-25
Ah, ok. I understand.

Ubuntu already has a settings editor in its repository:

Which NVIDIA driver do you have installed?
nvidia-glx or nvidia-glx-new?

If you have the **nvidia-glx-new** driver, look up "**nvidia-settings**" in the repository and install it.

Else, install the "**nvidia-xconfig**" package.

Regards
Iain

---

### Post by Prospero2006 on 2008-05-25
Post Retracted

---

### Post by asintu on 2008-05-25
> **tinivole said:**
> Ah, ok. I understand.

Ubuntu already has a settings editor in its repository:

Which NVIDIA driver do you have installed?
nvidia-glx or nvidia-glx-new?

If you have the **nvidia-glx-new** driver, look up "**nvidia-settings**" in the repository and install it.

Else, install the "**nvidia-xconfig**" package.

Regards
Iain

how do i tell which version I have?

---

