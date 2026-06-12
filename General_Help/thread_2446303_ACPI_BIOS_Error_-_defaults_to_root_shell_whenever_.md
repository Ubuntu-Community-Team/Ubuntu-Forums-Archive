---
title: "ACPI BIOS Error - defaults to root shell whenever I try to boot UBUNTU 20.04"
date: 2020-06-28
forum: General Help
---

### Post by aryasolves on 2020-06-28
I am unable to boot ubuntu in my laptop since yesterday. It is not even recognising any external USB which I can use to boot ubuntu. 
Below mentioned are the errors encountered:

ACPI BIOS Error (bug): could not resolve symbol [\_SB.PCI0.GFX0.DD02._BCL], AE_NOT_FOUND (20190816/psargs-330)

ACPI Error: Aborting method .... due to previous error

If somebody can help me resolve this, that'd be great. 
Thanks

---

### Post by CelticWarrior on 2020-06-28
The error is probably harmless, probably was always there but you didn't see it due to the splash screen and subsequent successful boot of the graphical environment.
Something must have happened for it now not being able to boot the graphical environment but whatever that is it has nothing to do with the ability to boot from external media. At this stage it's important NOT to confuse things that are totally unrelated.

---

### Post by aryasolves on 2020-06-29
Is there a way to fix this?
I have tried switching between the graphics kernel modules. I read that there is usually some problem with Radeon working on linux, so I tried using amdgpu but to no avail.
I am also getting MCE hardware errors in some instances. Rest of time, it just goes into emergency mode saying that the UVD is not responding.
Any help is greatly appreciated.
Thanks.

---

