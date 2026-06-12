---
title: "Linux users... please help... Booting problems"
date: 2007-07-17
forum: General Help
---

### Post by whabo on 2007-07-17
[SIZE="3"][SIZE="5"]Okay first of all i would like to thank youfor clicking on my post... 
- Well here is the thing.... i tried to install ubuntu on an external drive... didnt work well... so i shut down my external ... and rebooted my system.... then on reboot an error showed up ... error 21 and error 22 ( maybe linux errors)... and i could not get on windows.... what i did is that i placed teh live CD back into my system and partition my harddrive to run ubuntu and windows .... well it worked i dual booted with both ... but when i tried to reformat Ubuntu's partition and delete it so that i can use only windows ... teh same error 22 appeared .... right now teh only was i can get to windows is by dual booting with linux .... and i dont want that... this laptop is 3 years old .. and ubuntu doesnt really run appropriately on this machine... how can i remove ubuntu and make windows act as my primary OS.... please help... any suggestions would be appretiated.. i tried the IRC help .. but no1 helped me 
[/SIZE]

FOrmatting my windows .. partition is really not an option ... thank you for your help:confused:[/SIZE]

---

### Post by jfinkels on 2007-07-17
> **whabo said:**
> [SIZE="3"][SIZE="5"]Okay first of all i would like to thank youfor clicking on my post... 
- Well here is the thing.... i tried to install ubuntu on an external drive... didnt work well... so i shut down my external ... and rebooted my system.... then on reboot an error showed up ... error 21 and error 22 ( maybe linux errors)... and i could not get on windows.... what i did is that i placed teh live CD back into my system and partition my harddrive to run ubuntu and windows .... well it worked i dual booted with both ... but when i tried to reformat Ubuntu's partition and delete it so that i can use only windows ... teh same error 22 appeared .... right now teh only was i can get to windows is by dual booting with linux .... and i dont want that... this laptop is 3 years old .. and ubuntu doesnt really run appropriately on this machine... how can i remove ubuntu and make windows act as my primary OS.... please help... any suggestions would be appretiated.. i tried the IRC help .. but no1 helped me 
[/SIZE]

FOrmatting my windows .. partition is really not an option ... thank you for your help:confused:[/SIZE]

When you install Ubuntu, you also install GRUB, a boot loader which allows you to choose from which partition to boot, to the Master Boot Record (MBR) on your hard drive. This overwrites whatever files Windows originally wrote to the MBR. Consequently, to get your "Windows-only" boot, you will have to overwrite the MBR again, with the original data that Windows writes.

Unfortunately I do not have much experience with this. You may try searching the forums and searching using Google for reinstalling the Windows MBR (for your specific version of Windows).

---

### Post by phidia on 2007-07-17
[http://www.tech-recipes.com/rx/44/master_boot_record_mbr_fix_repair](http://www.tech-recipes.com/rx/44/master_boot_record_mbr_fix_repair)

When you installed ubuntu it installed grub to the mbr of your primary drive. Use the link above for instructions to reset your mbr.

In the future if you want to install ubuntu to an external or secondary drive use the alternate cd image.

---

### Post by whabo on 2007-07-17
HEY .... i fixed it .. thank you for everything...... WHat i did .. is as following 

booted my laptop with windows CD.....that came with my laptop.... i pressed any key to continue.
- then i pressed R to repair windows
- then typed ( 1 ) after asking me to choose an OS ... and 1 was my only choice ( WIN XP)
- then typed fixmbr as a command
- it displayed warnings .. buti movedon and pressed Y .. for yes
- then i typed exit  (on teh command line) after it was done
- rebooted and everything went back to normal
WHO EVER . experiences this ... TRY TO DO WHAT I DID .. it works .... i lost nothing .. thank god ... and windows boots with no problems ... after removing ubuntu...

THank you guys for your help...

---

### Post by colalord on 2007-07-18
i'm a long time windows tech.

what you did by using the windows repair console and running the fixmbr command is the best way to fix the problem you were experiencing.

fixmbr just rewrites the windows boot loader into the master boot record over grub (ubuntu's boot loader).

windows is kind of selfish, so if you re-install windows after installing ubuntu it will install the windows boot loader over grub as well.

---

### Post by jfinkels on 2007-07-18
> **colalord said:**
> [...]windows is kind of selfish, [...]

Windows is *very* selfish :D

---

### Post by jaymesh on 2007-08-19
Is it possible to edit the grub to boot windows? I installed Ubuntu and it erased the windows boot option totally, which I understand because it overwrote the grub. I want to be able to boot both windows and Ubuntu. Ive searched around the forums and have failed to find any helpful info. Can someone point me in the right direction?

---

### Post by vietunion on 2007-08-19
Read first comment, i think it can solve your problem

[http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/](http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/)

Sorry for my english

---

### Post by whistlerspa on 2007-08-31
If you want to delete grub from the mbr an easy way is to boot the computer to a command prompt by e.g. using an old win98 boot disk [if you have one]. 

then enter the command  fdisk /mbr.

On reboot (ctrl + alt + del) it'll boot straight into Windows.

---

