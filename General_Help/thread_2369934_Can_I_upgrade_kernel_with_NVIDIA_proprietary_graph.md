---
title: "Can I upgrade kernel with NVIDIA proprietary graphics installed?"
date: 2017-08-28
forum: General Help
---

### Post by linuxthunder on 2017-08-28
[FONT=verdana]Just installed Ubuntu 16.04.3 which runs the 4.10 kernel. My new rig is a Ryzen 1700 CPU and a lot of the new support for Ryzen chips is in kernel 4.12. I'm using an NVIDIA GeForce GTx 1050Ti with the proprietary driver installed.[/FONT]
[FONT=verdana]If I upgrade to kernel 4.12, will this break the graphics on the system? If so, what is the proper procedure for upgrading the kernel with proprietary graphics cards?[/FONT]
[FONT=verdana]Thanks[/FONT]

---

### Post by Autodave on 2017-08-28
If you installed the driver from the repositories, you should be OK. If you downloaded it from the internet you are *probably *still OK. However, it will never get upgraded. Also, you could lose the driver and have to reinstall it.

---

### Post by linuxthunder on 2017-08-28
I installed it from the repositories.

So it will never get upgraded if I upgrade the kernel?  I'm assuming there is a workaround when a new driver version is available?

---

### Post by linuxthunder on 2017-08-29
I upgraded to 4.12.9 with ukuu and all is working fine.

---

### Post by VMC on 2017-08-29
What does 'dkms status' show.

---

