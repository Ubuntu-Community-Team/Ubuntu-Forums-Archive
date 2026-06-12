---
title: "Grub unable to find partition."
date: 2013-04-29
forum: General Help
---

### Post by gabriella on 2013-04-29
OK I screwed something up :(
I'm sure there's a fairly easy solution to this so how do  I fix it? 

Here what I did. I had Ubuntu 13.04 installed on SDA1 and Xubuntu installed on SDA2. I used Gparted and deleted Xubuntu/SDA2 and expected that I'd need to update grub once I booted back up.

But..... It won't boot and tells me its "unable to find partition" I thought the boot loader from Ubuntu SDA1 was in control but obviously that got overidden by the installation of Xubuntu on SDA2 so the boot loader is confused. So how do I fix this, i.e remove the SDA2 bootloader so I'm back to just SDA1 again?

Thanks

---

### Post by oldfred on 2013-04-29
One of the easiest ways:
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

OR 
      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

 [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

---

### Post by gabriella on 2013-04-30
Thanks Oldfred!

Actually I figured it out myself using the method below if anyone else screws up like I did!

[https://sites.google.com/site/easylinuxtipsproject/grub](https://sites.google.com/site/easylinuxtipsproject/grub)

---

