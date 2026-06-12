---
title: "How to temporarily remove Ubuntu?"
date: 2013-03-19
forum: General Help
---

### Post by Nesaskewatch on 2013-03-19
Hi folks. I desperately need to do my taxes today, but do not have access to the windows 8 partition on my system. I have a dual boot, 12.10/Windows 8 UEFI laptop (Asus N56 variant) and lost the windows entry in grub yesterday after re-installing the root partition for Ubuntu. (I have a separate /home drive) Boot-Repair does not fix the problem for some reason, but that is beside the point right now. I wondered if there is some way to safely disable grub so windows boots again, then I can repair/replace grub later after I have done my taxes, or some other method that gives me access to the windows partition.

This is very time sensitive so any replies will be gratefully received. I just do not have the time to search around for some sort of fix that may or may not work or possibly wreck the entire system.

Thanks

---

### Post by oldfred on 2013-03-19
You should be able to directly boot from UEFI menu to Windows.

 /EFI/Microsoft/Boot/bootmgfw.efi 

Boot repair sometimes renames the above and adds  a backup of it to chain load from grub's menu. Boot-Repair then makes the above file the shim file from Ubuntu. Some UEFI are modified to only let the above file name boot, which is not correct but how it is. But since you do not have the backup that looks like the original Windows file & should let you boot it. You may need secure boot on. UEFI remembers last default boot and reuses that until you change that in the UEFI menu.

There is also a backup of the above file that you can just manually copy back into the efi folder and then boot from UEFI menu.
      
 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

What Boot-Repair does to rename files, but yours does not look renamed currently.
      
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.
User disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 
Backup files when renamed:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi

---

### Post by Nesaskewatch on 2013-03-19
You have been a saint Fred. We are all lucky to have you here, helping idiots like me. I love Ubuntu. I really do. I hate that I am being forced back in to the grasping tentacles of 8 but I have no choice. Ubuntu just does not run on my hardware without somebody knowledgeable enough to make it all work properly. I have failed... And I feel like crap. I did get windows working using your suggestion of enabling secure boot. I will see if I can find the boot line I used after enabling secure boot so others might benefit, but for now, it worked. I am going to fall into bed -- exhausted and well past my limit -- knowing I will only be a few hours late. At least I can sleep now.

Thanks old son.

Edit: Just for the record, I had to hold the esc key to get into the boot device selection and select "Windows Boot Manager [insert hdd manufacturer here]". Then it boots into 8. I will try to disable secure boot and see if I can run Ubuntu in the morning. A clunky way of doing it but it might just work.

---

### Post by oldfred on 2013-03-19
Glad that worked. 

Hope Ubuntu works, but some just have to have secure boot off or use the rename as UEFI only boots the Windows file.

---

### Post by Nesaskewatch on 2013-03-20
I can still boot into Ubuntu but I have to go into the bios and disable fast boot and enable Launch CSM, as well as disable secure boot, save and exit then select Ubuntu from Grub. Again, it's clunky but it works. I much, much prefer using Ubuntu, so I will leave things as they are now and repeat the bios shuffle when I must run 8. I am still perplexed as to why Boot-Repair failed to do its magic this time after working so well before, but that is another matter that will likely be resolved with time. It is unfortunate that manufacturers are making it such a nuisance to run Ubuntu. While 8 is somewhat of an improvement it is still far too intrusive, gives even less user control, no longer offers many needed applications out of the box and has way too many aspects that are downright counter-intuitive. Ubuntu is vastly superior to 8 in virtually every respect. 

Again, thanks Fred.

Edit: how on earth does one mark the thread as solved now? I cant find it anywhere...

---

### Post by oldfred on 2013-03-20
There seem to be a few UEFI that will not boot anything but Windows 8 in secure boot. But that is wrong. Your vendor should eventually have a UEFI update that fixes that. 
Microsoft does require vendors to let a user turn secure boot off, but otherwise does not specify much. The entire purpose of UEFI to to allow multiple booting from an efi partition.


Boot Repair should convert a BIOS (CSM) install to UEFI and let you boot that way. Then for some UEFI that only boot the Microsoft file Boot-Repair renames files as a work around. But yours may be one that even that does not work. Or it can be just all the combinations of settings in UEFI menu and how Ubuntu is installed. 

But if it is working ok for you it may not be worth the effort to resolve all the issues.

---

### Post by Nesaskewatch on 2013-03-20
> **oldfred said:**
> But yours may be one that even that does not work.

But it did, and for quite a while. I used Boot-Repair at least a half dozen times to repair the dual-boot after re-installing the / partiton of 12.10 and it worked perfectly time after time. It was just the last install that Boot-Repair would not finish the job and just sat there with the little bar/blob going back and forth. Oh well, as you so eloquently say:> **oldfred said:**
> But if it is working ok for you it may not be worth the effort to resolve all the issues.

I sure hope it isn't worth bothering with. I dont mind messin with the setup to get 8 to boot as I hardly ever use it. But I just know that some day I'm gonna push the wrong button and wreck the whole works. It's inevitable... I can intuitively fix just about any machine there is with my bare hands, but I just cant seem to do anything software related on my computers without borking them all to blazes. ](*,)

---

