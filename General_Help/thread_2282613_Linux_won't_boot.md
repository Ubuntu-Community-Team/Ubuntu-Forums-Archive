---
title: "Linux won't boot"
date: 2015-06-15
forum: General Help
---

### Post by KingNeil on 2015-06-15
I have a Windows 8 computer (pre-installed with Windows 8)

It is a Fujitsu LIFEBOOK A512

I am trying to boot Linux from a CD.

I have tested that the CD works on another computer in the house.

But it won't boot on this one.

I have heard that Smart boot is the reason for this, and also, Fastboot.

So, I went into the BIOS.

And I disabled Smartboot.... and I disabled Fastboot.

But despite doing this, it still won't boot.

This computer simply will not boot Linux.

It is Lubuntu 15.04.

What should I do??

---

### Post by ajgreeny on 2015-06-15
What version of Linux; is it 32bit or 64bit, as it must be 64bit if Windows 8 is installed in UEFI mode, which it will undoubtedly be, I suspect.

---

### Post by leunam12 on 2015-06-15
Have you enabled legacy boot? Also try a USB stick instead of a DVD.

---

### Post by michael136 on 2015-06-15
Check Boot Priority In Your Bios

---

### Post by KingNeil on 2015-06-15
> **ajgreeny said:**
> What version of Linux; is it 32bit or 64bit, as it must be 64bit if Windows 8 is installed in UEFI mode, which it will undoubtedly be, I suspect.

Are you saying that I should use a 64-bit Linux if I want it to work? It wasn't clear what you meant.

> Have you enabled legacy boot? Also try a USB stick instead of a DVD.

Are you saying that I should enable legacy boot?

And yes, I've tried a USB, and that doesn't work.

> Check Boot Priority In Your Bios

Not needed. I  just select the CD from the drop down list.

---

### Post by ajgreeny on 2015-06-16
> **KingNeil said:**
> Are you saying that I should use a 64-bit Linux if I want it to work? It wasn't clear what you meant.Yes, you do need 64bit if using UEFI



> Are you saying that I should enable legacy boot?No, not if Windows is in UEFI mode, or you will not be able to boot Windows
> And yes, I've tried a USB, and that doesn't work.I wonder why that is. have you ever been able to boot from a USB properly made as a boot disk?
> Not needed. I  just select the CD from the drop down list.Fair enough!

I know so little about Windows, particularly Windows 8, that I will leave others to help you more with this.

---

### Post by Vladlenin5000 on 2015-06-16
> **KingNeil said:**
> Not needed. I  just select the CD from the drop down list.

Make sure you select the UEFI option, if more than one (DVD or USB)-> requires CSM enabled and it shouldn't be needed, you want UEFI mode for your dual-boot.
Your model may need setting a supervisor password in order to unlock advanced features at UEFI system settings like secure boot. Disabling it shouldn't be necessary nowadays but there's always the odd model...

---

### Post by KingNeil on 2015-07-10
OK guys. Here's is the full solution....

1. go to BIOS and set a supervisor password
2. disable Secure Boot
3. enable CSM

Then Linux boots... That's it..!

The one thing I was missing before was CSM.

All done.

---

