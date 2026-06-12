---
title: "Reconfigure kernel?"
date: 2006-11-09
forum: General Help
---

### Post by codypumper on 2006-11-09
Hey, is there any way I can reconfigure the latest kernel installed on my system?

---

### Post by dcstar on 2006-11-09
> **codypumper said:**
> Hey, is there any way I can reconfigure the latest kernel installed on my system?

Yes, download the source and recompile it yourself.

There are many "HOWTOs" on this subject, do a forum search for them if you want the details.

---

### Post by codypumper on 2006-11-09
Can I do this from the second boot option for the first boot option? :-k

---

### Post by dcstar on 2006-11-09
> **codypumper said:**
> Can I do this from the second boot option for the first boot option? :-k

I don't quite understand the question, but you can have as many different kernels installed and available in your boot menu as you like.

You can also edit your /boot/grub/menu.lst file and make multiple entries of the same kernel with varying boot command options.

---

### Post by codypumper on 2006-11-09
Can i reset the initrd file somehow?

---

### Post by dcstar on 2006-11-09
> **codypumper said:**
> Can i reset the initrd file somehow?

If you want a new copy of that file, reinstall the kernel using Synaptic.

---

### Post by codypumper on 2006-11-10
Is there a specific way to reinstall the kernel from synaptic?

---

### Post by kinematic on 2006-11-10
mark it for re-installation ;)

---

### Post by codypumper on 2006-11-10
alright, thanks

---

