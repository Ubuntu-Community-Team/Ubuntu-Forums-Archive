---
title: "Dual boot problem"
date: 2016-07-25
forum: General Help
---

### Post by pascal.malouin on 2016-07-25
Hi,

I installed Kubuntu 16.04 succesfully on a WD My Password Ultra 2 Tb external hard drive partition.

I use it to boot linux from the external hard drive from home (Windows 10) and work (Windows 7).

It used to boot perfectly on both PC, but for some reason, now I can't boot on my work PC anymore (nothing changed on either PCs)

**Home PC**

I boot using UEFI and it works every time.

**Work PC**

When I try UEFI ubuntu from the boot menu, it does nothing. It just gives me the boot menu again.

When I choose legacy booting, it gives me **boot - error: file '/grub/i386-pc/normal.mod' not found** and prompts Grub rescue.

When searching for normal.mod, I find it located in /grub/x86_64-efi/ which is, as I understand, the path for UEFI booting.

I looked on the net to find a solution, but since I'm a newbie at both dual booting and linux, I can't find the answer I'm looking for.

So, how do I get to boot on both PC, just like before?

---

### Post by QIII on 2016-07-25
Have you asked your employer/IT/IS for help with your work computer?

---

### Post by pascal.malouin on 2016-07-25
Hi QIII,

No I didn't. I have admin rights on my machine.

Thanks

---

### Post by QIII on 2016-07-25
It may seem as though nothing has changed, but IT/IS may have pushed an update or policy that conflicts.

You may want to ask about that.

---

