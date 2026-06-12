---
title: "Installing on non-mac UEFI system"
date: 2007-08-17
forum: General Help
---

### Post by gabeyg on 2007-08-17
Hi! And actually, I am not using Mac or iMac, but I'd like to test UEFI. The question is following:
1. How can I install UEFI or similar firmwares? (Or how can I access either RAM or ROM that stores my BIOS?)
(i know what i will have consequences.)
2. Is GParted supports GPT when creating and shrinking partition without having MBR?
3. Is there GRUB 0.97 patch that allows it to be installed in GPT parts and boot from it and reconginze disk that use GPT shemes
4. Does ubuntu cd allows it to install on GPT partition?
5. if either GParted supports GPT, how can I make my partition to be GPT/MBR Hybrid for installing windows?
Thanks a lot. I have benefited from this forum. Now, I learned a lots of things about ubuntu, linux, windows, programming etc. If i became a genius in computer, I will contribute as you did.

---

### Post by aldenhg on 2007-08-17
You've misunderstood what EFI is. EFI (nee UEFI) isn't something that you can "test out." It is a total replacement for the BIOS that is put on the motherboard by the manufacturer. In fact, unless you have an Intel Mac of some sort, you probably don't even have the capability to use EFI. It's possible that if you're running an Itanium server that you have it, but what it boils down to is that you don't need to worry about it. Either it's there or not.

---

### Post by gabeyg on 2007-08-18
> **aldenhg said:**
> You've misunderstood what EFI is. EFI (nee UEFI) isn't something that you can "test out." It is a total replacement for the BIOS that is put on the motherboard by the manufacturer. In fact, unless you have an Intel Mac of some sort, you probably don't even have the capability to use EFI. It's possible that if you're running an Itanium server that you have it, but what it boils down to is that you don't need to worry about it. Either it's there or not.
OK, if not, and since i have mac (though I don't use mac a lot i use pc), eliminate first question and about other questions.

---

### Post by gabeyg on 2007-08-18
> **gabeyg said:**
> OK, if not, and since i have mac (though I don't use mac a lot i use pc), eliminate first question and about other questions.
Also, the thing is that about accessing RAM or ROM that stores BIOS. since my pc is new, I can update BIOS any time.  So, how can i access them? You have to access BIOS in order to update or install such things as LinuxBIOS or OpenBIOS!

---

### Post by aldenhg on 2007-08-18
Why do you want to uppdate your BIOS? Can you not get any sort of Linux to load up? The BIOS isn't exactly the part of the computer you want to be dinking around with if you don't need to. If you mess up just a little you'll brick your motherboard. I don't specifically know how to do it, but a quick Google search with your motherboard model and "flash linux" should yield good results.

---

