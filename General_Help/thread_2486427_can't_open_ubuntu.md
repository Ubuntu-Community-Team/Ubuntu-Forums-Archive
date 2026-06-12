---
title: "can't open ubuntu"
date: 2023-04-30
forum: General Help
---

### Post by stonefly4 on 2023-04-30
I installed ubuntu on this computer years ago. I split the hard drive. When I turned on the computer, the first screen gave me a choice to boot into ubuntu or windows. The computer hasn't been used in years. I just dug it out and turned it on. It boots right into windows without the option to choose ubuntu.

What happened?

---

### Post by yancek on 2023-04-30
No way for anyone here to know without more information.  If you cannot boot into Ubuntu on the computer, you would need to create a bootable usb with an Ubuntu iso file, then boot that and go to the boot repair site below and download it and run it by selecting the 2nd option (using the ppa) and then using the Create BootInfo Summary option and posting the link you get when it finishes here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It seems an unlikely scenario.  How was it stored?  Could someone else have used it?

---

### Post by stonefly4 on 2023-04-30
thank you

---

### Post by Impavidus on 2023-04-30
If the computer hasn't been used in years, the version of Ubuntu may be old and unsupported and I wouldn't expect any important files there. Just do a fresh install to put the computer in a known, clean state.

---

### Post by grahammechanical on 2023-04-30
Microsoft will not allows its Windows operating system to dual or multi-boot with any other OS that is not a Microsoft OS. Updates to earlier versions of Windows had a habit of over writing the Grub boot files. 

The recommendation to use Boot Repair to produce a boot summary that you can link to so we can view it is a good recommendation. We do not like making suggestions without sufficient information. We might make matters worse. You may need to reinstall the Grub boot files. We can not know that unless we see that Boot Summary.

Regards

---

