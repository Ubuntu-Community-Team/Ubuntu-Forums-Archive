---
title: "fixing grub after triple boot"
date: 2007-05-10
forum: General Help
---

### Post by yamokojc on 2007-05-10
not long ago I set my box up as a triple boot (XP/Vista/Ubuntu). when grub loaded i had the option of loading ubuntu or the windows loader. if i selected the windows loader then i had the option of xp or vista via the vista boot loader.

after some time i realized that vista was basically just taking up valuable disk space so i decided to dump it and give the rest of the partition to ubuntu.

now i have two separate hard drives, one with xp and one with ubuntu. everything works great except my grub menu still has the same exact options as before. and so i still have to load xp by going through the windows boot loader.

so my question is how can i fix this so that i can boot xp or ubuntu from the main grub menu?

---

### Post by Herman on 2007-05-10
Hello yamokojc,
Do you mean you want to be able to boot Windows XP a little bit more quickly without having to see the ugly NTLoader boot menu? 
Grub does not try to be able to boot a Windows kernel directly, Grub only chainloads Windows. (It meets the Windows NTLoader 'halfway', at the Windows 'bootsector', and hands over control to NTLDR to boot Windows. Therefore you cannot do without NTLDR, but you can do without having to look at the boot menu for it.

I think you just need to edit your boot.ini in Windows XP for that. Probably you should just delete the old line or lines for Vista that are now redundant in there. I'm not an expert on boot.ini, it is a finicky file to edit, you can easily make your Windows unbootable, so be careful and maybe check other sources of information about how to edit boot.ini in Windows XP.
Before editing boot.ini in Windows, I recommend you see the following link and download a Super NTLDR CD Disk or a floppy disk, to make sure you will still be able to boot even if an error occurs, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm")

Regards, Herman :)

---

### Post by yamokojc on 2007-05-22
Thanks for the reply Herman.

It seems that the real problem here is that the windows boot loader still thinks Vista is installed. When the windows boot loader pops up there is an option to boot into Vista (I have yet to select it now, I am scared of what will happen). However, I checked my boot.ini file and it is setup for a single boot (just XP). So, I guess the question is now, where is Windows looking that it still thinks Vista is installed? And how can I prevent it from looking there.

I realize that this is a Windows issue now, but if anyone can help I appreciate it. If not, does anyone know of a decent windows forum where I can post this?

Thanks in advance.

---

