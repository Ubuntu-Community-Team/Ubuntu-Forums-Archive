---
title: "ACPI PCC probe failed.Stuck in reboot loop"
date: 2015-05-08
forum: General Help
---

### Post by indyeah on 2015-05-08
Hi all

I recently upgraded my laptop from 14.10 to 15.04.The grub version is 3.19.

Recently after hard shutdown,when i try to boot into Ubuntu i get the error "ACPI PCC probe failed".Disk check ensures and then i am dropped to root terminal screen.

I really don't have any idea how to boot normally into ubuntu from therein.I am stuck in infinite reboot loop.Trying to go into recovery mode does nothing.

Please help

---

### Post by indyeah on 2015-05-09
Anyone with a solution.My work is getting affected due to this.

---

### Post by dino99 on 2015-05-09
the acpi pcc error can be ignored; that only mean your hardware is missing the said chipset/feature introduced with recent kernels (3.19 & up)
the most recent grub is 2.02beta2-22

so your issue is not related to the above ; try the 'recovery mode' from the grub menu, activate the network and open a terminal, then try to fix the installation and check /var/log/syslog or journalctl

---

### Post by indyeah on 2015-05-09
@dino99
i can definitely open the network and terminal but how to "fix the installation"

TIA

---

### Post by nns2006 on 2015-05-10
> **indyeah said:**
> @dino99
i can definitely open the network and terminal but how to "fix the installation"

TIA

I solved this problem by removing the kernel 3.19.0-17 completely from synaptic manager. For me this happens after updating the kernel. If you haven't removed the kernel 3.19.0-16, your system will boot with this. This seems to have solved my problem. Hope it helps.

---

### Post by kushal4 on 2015-08-27
Use Indain Ideas buddies,  start your computer hold shift, when this dialogue box opens (ACPI PCC probe failed) all you have to do is type exit and hit enter.... All things will be solved with ease

---

