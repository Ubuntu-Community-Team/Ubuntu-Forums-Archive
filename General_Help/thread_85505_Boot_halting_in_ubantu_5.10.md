---
title: "Boot halting in ubantu 5.10"
date: 2005-11-02
forum: General Help
---

### Post by jrlinux711 on 2005-11-02
I am trying to set-up a dual boot pc using a Dell Dimension 2350 with 768 MB RAM and 2 - 40 GB hard drives.  I have also added a GE-Force FX5200 video card with graphics by nVidia.  One hard drive is set as the Master with Windows XP installed and the other hard drive is the Slave with Ubuntu 5.10 installed.  This Slave drive is a secondary slave on an IDE cable with the Master being my DVD/CD Writer drive - Is this OK.

The install for both went well - I get the GRUB screen allowing me to choose which OP SYS I want and Windows XP boots and works well.  However when I choose Ubuntu 5.10 the boot process proceeds until the line STARTING HOTPLUG SUBSYSTEMS and the hard drive stops working and the boot process comes to a halt.  Any assistance you can provide would be appreciated

Jr

---

### Post by adwait on 2005-11-02
Try skipping the hotplug system by pressing Ctrl + C when it appears.

---

