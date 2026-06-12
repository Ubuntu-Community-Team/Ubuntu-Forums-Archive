---
title: "Now W7 won't boot, only purple screen"
date: 2018-10-06
forum: General Help
---

### Post by rva1945 on 2018-10-06
Hi:

I have dual boot (GRUB) and so far it worked well with Windows 7 and Ubuntu 12.04 LTS. But after Ubuntu refused to shut down, I had no other option that reset button and now when choosing Windows as the O.S. I just get a purple screen. If I choose Ubuntu, it boots ok.

Thanks,
Robert

---

### Post by yancek on 2018-10-06
Ubuntu 12.04 hasn't been supported for over a year so you might think about upgrading.

Download and run boot repair from the site below and select the option to create boot info summary and do NOT try to make repairs.  Post the link you are given when boot repair finishes here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by yuioni on 2018-10-09
i recently went through this same problem. this solution fixed my problem.

----------------------------------------------------------------------------------------------------------------------
If it is booting into Linux, you could try to update grub.
In terminal enter sudo update-grub
Make sure all of your OS drives are enabled. This will search for the Windows install and add it to the grub bootloader.
If it is just booting into windows, check to make sure boot order is set correctly in bios. You want your primary boot drive to be your Linux drive.
----------------------------------------------------------------------------------------------------------------------------------------

after that, restart and if the grub boot loader helped, you should have the option to boot into both OS's again. (edit) mine was for lubuntu 18.04.

---

