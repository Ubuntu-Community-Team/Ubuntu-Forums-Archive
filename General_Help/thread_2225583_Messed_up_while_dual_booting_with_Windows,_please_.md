---
title: "Messed up while dual booting with Windows, please help!"
date: 2014-05-22
forum: General Help
---

### Post by kuverit on 2014-05-22
Hi all,

I made a silly mistake. I was following this tutorial: [http://www.linuxbsdos.com/2012/06/06/how-to-dual-boot-linux-mint-13-cinnamonmate-and-windows-7/2/](http://www.linuxbsdos.com/2012/06/06/how-to-dual-boot-linux-mint-13-cinnamonmate-and-windows-7/2/)
I made a partition which was mounted at /boot. But I mistakenly forgot to select that partition as the Device for boot loader installation. I will copy the part from the article below:
> The final task that must be completed at this step before clicking **Install Now**, is to select the **Device for boot loader installation**. By default, it is **sda** or to be exact, the MBR of sda. You need to change that to sda3, which corresponds to the boot partition that you just created.
[IMG]http://www.linuxbsdos.com/wp-content/uploads/2012/06/MintInstall11-600x371.png[/IMG]

 This is what the **Device for boot loader installation** dropdown menu should look like before you click **Install Now**.
[IMG]http://www.linuxbsdos.com/wp-content/uploads/2012/06/MintInstall12-600x371.png[/IMG]



I forgot to do the above step. And because of that, now GRUB is being used as my boot manager, instead of Windows's Boot Manager. Is there any way to move the boot loader into the /boot partition? I want to use the Windows Boot Loader and not GRUB.

Please help me. Thanks in advance.

---

### Post by mastablasta on 2014-05-22
does it work? if it does just leave it. there is nothing wrong with using grub.

thgis is how it now loads - 
BIOS/UEFI - > GRUB -> LINUX
BIOS/UEFI - > GRUB -> Windows boot loader - WINDOWS 

otherwise yes it is posisble to remove GRUB (search internet for "restore MBR windows"), you would then need to reinstall grub manually to where you want it. but like i said if it works then there is nothing wrong with your current setup. if you ever decide not to use linux anymore just restore the MRB using windows command.

you will need grub somewhere anyway to launch linux. since windows boot loader can only load windows.

---

### Post by kuverit on 2014-05-23
Thanks mastablasta for your help. You correctly identified my situation. For now I'm leaving it as it is, as you suggested. But just out of curiosity, can you point me to some articles/tutorials on how to reinstall grub where somebody would want?

Thanks again.

---

### Post by dragonfly41 on 2014-05-23
Grub Customizer should help you in customising grub menu.

---

