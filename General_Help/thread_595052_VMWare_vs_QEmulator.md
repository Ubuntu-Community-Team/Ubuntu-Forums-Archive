---
title: "VMWare vs QEmulator?"
date: 2007-10-28
forum: General Help
---

### Post by dmontalvao on 2007-10-28
Hi there!

This is the first time I install a virtual machine on my computer (I use Gutsy), and I've chosen QEMU because it is free - as far as I could understand VMWare Player is free, but not the Workbench, and I couldn't understand the differences.

Does anyone ever tried to compare both these emulators? Plz feel free to post your opinions on this subject! I would appreciate it very much.

Thank you very much.

---

### Post by Cochise on 2007-10-28
ive used both, and find neither of them as good as virtualbox check it out at virtualbox.org

---

### Post by hamster_billy on 2007-10-28
Never used either, but I have Innotek VirtualBox installed. It does anything I'd want it to do, and I'd say I does it pretty well, though admittedly I have nothing to compare it to.

---

### Post by fjgaude on 2007-10-28
I've used VirtualBox and VMServer for sometime. VirtualBox doesn't permit clipboarding between WinXP and Linux, only permits the NIC to see 10Mb/s. VMware Server sees 1000Mb/s and permits clipboarding. Both are fine for speed, except if you wish to have large file interaction between WinXP and Linux. (Notice my signature.) <smile>

Both are free, yes. The Server is about like the Workstation, the latter costing money. BTW, neither is ready from the repos under Gutsy. I downloaded VMware Server from the VM site. It installs easily on Gutsy with all the tools and extensions. Vbox is not ready yet, as far as I can tell.

Now if anyone has gotten vbox to work at speeds, NAT above 10Mb/s please say how you did it.

---

### Post by hamster_billy on 2007-10-28
My VirtualBox (WinXP guest on Ubuntu host, with Guest Additions installed) syncs the clipboard. It occasionally will screw up (never on Gutsy so far; cross fingers) and paste weird characters; then the clipboard will only work properly again after a reboot. Never worried about network speed though - nothing I can say there.

---

### Post by dmontalvao on 2007-10-29
Thank you all for the help!

Atm, I am trying VBox, because I don't really understand VMWare - as far as I could get, VMWare will not be available for i386 machines like mine anymore (Synaptic),

Anyway, comparing Qemu (even with Kqemu) with Vbox, in terms of speed... There is no comparison possible. In my machine, installing WinXP in Vbox is almost "real time". With Qemu, it took ages!! I haven't done any more comparisons yet (I am still installing WinXP with Vbox).

Thanks again for all your help!

___________
I will neither dual boot nor use windows!!! :)

---

### Post by Dr. Nick on 2007-10-29
> **dmontalvao said:**
> Thank you all for the help!

Atm, I am trying VBox, because I don't really understand VMWare - as far as I could get, VMWare will not be available for i386 machines like mine anymore (Synaptic),

Anyway, comparing Qemu (even with Kqemu) with Vbox, in terms of speed... There is no comparison possible. In my machine, installing WinXP in Vbox is almost "real time". With Qemu, it took ages!! I haven't done any more comparisons yet (I am still installing WinXP with Vbox).

Thanks again for all your help!

___________
I will neither dual boot nor use windows!!! :)



How did you setup kqemu? I use qemulator and ticked the checkbox to use kqemu and it was dog slow. However after following a guide on the wiki about loading the kqemu kernel  modules etc i really noticed a speed increase. My laptop doesnt support KVM but I am trying it on my desktop to see how it preforms.

Ill post links back here once I find them again

---

### Post by dmontalvao on 2007-10-29
Well... This is just for the record if anyone has the same questions.

I just installed Abaqus and Solidworks on WinXP-SP2 using VBOX on Gutsy, and they seem to work just fine (a bit slowly, but if you want to deal with heavy projects, I think Dual Boot is the option).

Now I need to try Labview aswell, but I cannot do it today.

Thanks again for all the help you gave me!

---

### Post by dmontalvao on 2007-10-29
> **Dr. Nick said:**
> How did you setup kqemu? I use qemulator and ticked the checkbox to use kqemu and it was dog slow. However after following a guide on the wiki about loading the kqemu kernel  modules etc i really noticed a speed increase. My laptop doesnt support KVM but I am trying it on my desktop to see how it preforms.

Ill post links back here once I find them again

I did that, but either I did it wrong or no good results were observed. Atm I am using VBox, and I haven't experienced any problems or incompatibilities (yet! cross fingers!).

---

