---
title: "Can I ghost a Win10 C: to a new disk with Ubuntu?"
date: 2022-02-05
forum: General Help
---

### Post by palteater on 2022-02-05
Hello

I use Ubuntu at home for most everything, but I have a Win10 work PC where the HDD starts to fill up.

Looking at ghosting the partition to a larger drive, but all the solutions I google are about downloading and using stuff named like ÜberBackup6000.exe that I suspect are either malware or totally unnecessary.

So: if I boot the Win10 PC with Ubuntu-on-a-stick, can I rely on **dd** or similar in a terminal to work for this operation? Or will that b0rk up some arcane BIOS thingamagig that MS conjured up to make life harder for us?

Is there even some way to resize the partition to fill the new drive via the Linux terminal?

---

### Post by dragonfly41 on 2022-02-06
If you have a work PC my suggestion is that you invest in an [external SSD]("https://uk.crucial.com/products/ssd/portable-ssds") provided that you have a USB 3.0 fast port on your PC. Even in my home setup I prefer running Ubuntu on external SSD's. This approach also distances Ubuntu from Windows machinations.

---

### Post by palteater on 2022-02-10
Not sure what you mean by that.

Let me clarify the situation:

The work PC is a CAD/FEM station that needs performance. It is actually a Threadripper Pro with 128 GB 8-channel RAM.
I want to put its current NVMe M.2 C: drive together with three identical ones on a PCIe RAID card, and use a new stick for boot. Thus, the old C: will become a hilariously fast and four times larger D:

What I desire to **not** do however is reinstall all the CAD/FEA suites and various assorted other programs, plus updating Windows 10 - because that does not only take time, it also requires me to do a shipload of reconfiguring whatever settings I have painstakingly set up right now. So I'd like to just ghost the boot drive onto a new one that might be larger as well.

So: my plan is to put in the new stick, boot from USB into Ubuntu, and use dd to clone the C: drive. And I wonder if that is the proper method, or if I will fall down some rabbit hole I do not know of?

---

### Post by linux-sysop on 2022-02-10
I am not going to preach at you about license agreements ( one license one copy ) but yes Gparted can clone partitions or even entire drives as long as the empty space is equal to or larger.

After that, it is between you and your EULAs.

---

### Post by tea for one on 2022-02-10
> **palteater said:**
> but I have a Win10 work PC where the HDD starts to fill up
If this is a work PC with Windows 10, has your employer not provided you with Windows utilities/software to help?
> **palteater said:**
> So: if I boot the Win10 PC with Ubuntu-on-a-stick, can I rely on **dd** or similar in a terminal to work for this operation? 
DD is pretty reliable but it may be worth looking at other software e.g. Clonezilla or Windows specialist tools like Acronis, Macrium inter alia.
Cloning is not a trivial process and 100% success rate is certainly possible. You will not know until you have booted into the clone and double-checked everything.
> **palteater said:**
> Or will that b0rk up some arcane BIOS thingamagig that MS conjured up to make life harder for us?
Impossible to answer without thorough knowledge of your UEFI/BIOS and the exact set up of your PC.
> **palteater said:**
> Is there even some way to resize the partition to fill the new drive via the Linux terminal?
Use Windows Partition tools to resize Windows partitions.

---

