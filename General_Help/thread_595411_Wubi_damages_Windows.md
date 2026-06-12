---
title: "Wubi damages Windows?"
date: 2007-10-28
forum: General Help
---

### Post by TorontoStorm on 2007-10-28
I've read that Wubi is more prone to be damaged if the power goes out. Does this only damage Ubuntu or damage the whole drive (meaning Windows will be unbootable or corrupted)? Also, is there ANY way that the whole drive becomes corrupted or something (I just want to know if Wubi ever poses a risk to Windows, I don't mind if anything happens to Wubi & Ubuntu) By the way, I'll be installing Wubi Ubuntu 7.10 (once its stable) with Vista Home Premium.

---

### Post by ago on 2007-10-29
> **TorontoStorm said:**
> I've read that Wubi is more prone to be damaged if the power goes out. Does this only damage Ubuntu or damage the whole drive (meaning Windows will be unbootable or corrupted)?

When the power goes out you always risk corrupting any filesystem which is in use at that 
moment, whether you use Wubi or not. Since Wubi sits on top of the windows filesystem, that too becomes vulnerable. That is independent of Wubi. If you turn off the power while you are copying a large file in windows, you'd also have a high chance of ending up with a corrupted filesystem. There are tools like chkdsk that can recover the situation. Of course that means that if you install Wubi on the D: drive and have windows in C:, a power outage can only affect D.

---

### Post by Computer Guru on 2007-10-29
Bottom line: Wubi poses no additional risk to your underlying *Windows* installation.

---

### Post by TorontoStorm on 2007-10-29
> **ago said:**
> When the power goes out you always risk corrupting any filesystem which is in use at that 
moment, whether you use Wubi or not. Since Wubi sits on top of the windows filesystem, that too becomes vulnerable. That is independent of Wubi. If you turn off the power while you are copying a large file in windows, you'd also have a high chance of ending up with a corrupted filesystem. There are tools like chkdsk that can recover the situation. Of course that means that if you install Wubi on the D: drive and have windows in C:, a power outage can only affect D.
Lets say I have Vista on C: how do I install Wubi on E:?

---

### Post by ago on 2007-10-29
> **TorontoStorm said:**
> Lets say I have Vista on C: how do I install Wubi on E:?

If you already have an E: drive, you select that in the installation dialog. If you only have a C drive, you either install on C, or you have to resize C and create a new partition. But if you do that, it better to install Ubuntu via LiveCD. Installing on C is not such a big deal, just avoid hard reboots and if they happen, run chkdsk.

---

