---
title: "how to make virtual box use video memory from NVIDIA graphics card?"
date: 2015-05-03
forum: General Help
---

### Post by ltorvalds11 on 2015-05-03
[IMG]http://i.imgur.com/J9JtXyV.png[/IMG]

[FONT=Helvetica Neue]as you can see virtual box is using [/FONT]**Video Memory**[FONT=Helvetica Neue] from Intel HD graphics.[/FONT]
[FONT=Helvetica Neue]How do I make it use memory from my Nvidia graphics card which has 2Gb memory much bigger than Intel's 128Mb ?[/FONT]

---

### Post by QIII on 2015-05-03
Hello!

Actually, that is the amount of memory assigned by the virtualization software and has nothing to do with the physical hardware.  Virtualbox (and VMs in general) provides what is known as a "hardware abstraction layer".  It doesn't run on your physical hardware.  The virtualization software brokers the communication between your virtual machine and the physical hardware, so you won't be able to directly access your graphics hardware.

KVM virtualization can provide better access to your graphics hardware, but it is still not perfect.

---

