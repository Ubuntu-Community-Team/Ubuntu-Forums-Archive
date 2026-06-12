---
title: "Dual boot Windows 7 (64bit) ubuntu 12.04"
date: 2013-01-27
forum: General Help
---

### Post by viBritannia on 2013-01-27
My laptop is a Acer Aspire dual booting Windows 7 (64bit) ubuntu 12.04 i tried installing grub on ubuntu with the terminal and i messed up and just shut my laptop down cause i was sick of it. The next morning when i started my laptop up it gave me my boot screen and then pop'd-up :
GRUB loading.
error: no such device: 9b16030c-08f8-4f5d-b228-63e13bca7839.
Entering rescue mode...
grub rescue>

While attempting to acces system recovery etc it wouldnt let me my screen would just freez and make a error beep noise.
Uppon typing 'ls' in grub rescue> it shows (hd0) and nothing more, uppon typing 'ls (hd0)/ in grub rescue> it shows error: unknown filesystem. All help is welcome for the record, my laptop didn't came with a live CD.

---

### Post by oldfred on 2013-01-27
Welcome to the forums.

Best to see what is where. Also this may offer to repair install.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

