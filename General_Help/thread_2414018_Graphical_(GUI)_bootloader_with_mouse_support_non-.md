---
title: "Graphical (GUI) bootloader with mouse support non-uefi"
date: 2019-03-05
forum: General Help
---

### Post by jonas740 on 2019-03-05
Hello there.

I have two OS on my machine. Windows 10 one one drive and Ubuntu 18.10 on the other drive. 

I was wondering if there is any way to add a GUI bootloader with mouse support instead of Grub 2.

I know Burg was used before but that aint working anymore it seems. Not for Ubuntu 18.10 Anyway. 

Or is there a way to have a GUI on the Windows partition with mouse support? 

Either way works. 

I found "refind" but that requires UEFI/EFI. And my installs are Legacy. 

Very important that it is mouse support in the bootloader.

---

### Post by DuckHook on 2019-03-06
Welcome to the forums, jonas740.

I can't be of much help I'm afraid, but for what it's worth, here are some thoughts and observations:

[LIST=1]
[*]***Do not use BURG.*** It has been out of development for years, is not maintained and is now a fossil.
[*]I do not know of any Windows boot loaders that play nice with other OSes. It seems that Windows is intent on maintaining their desktop supremacy and make no effort to accommodate dual boots.
[*]The boot loader is run very early in the boot process and needs to be lean and mean. Though technically there may be room for such graphical niceties as mice support, devs would likely treat such functionality as unnecessary extravagances. I am not familiar with any mouse supported boot loaders in Linux, though admittedly, the last time I did any research of this sort was more than three years ago. The landscape may have changed since I last checked.
[*]If you find one, you will have to replace GRUB. This is a fraught exercise. It is not impossible, but is usually considered a power-user customization. Be aware that breakage is common—which, in the case of a bootloader, usually means not being able to boot at all. If you are new to Linux, this is a real concern. Tweak at your own risk.
[/LIST]

---

### Post by jonas740 on 2019-03-06
Thank you for responding.

As you said there does not seem to excist any GUI bootloader for Linux. Well not for legacy use anyway.

But I actually managed to solve my problem with EasyBCD where i could add my Ubuntu drive as the second OS. And using Metro bootloader allows for using mouse in the bootloader. 

It was very easy to use and it works like intended. 

Why i wanted a bootloader that supports mouse is because i use a bluetooth keyboard.

---

### Post by DuckHook on 2019-03-06
Thanks for sharing your solution. I was not aware of this answer. I learn something new every day!

I have marked this thread "solved" for you.

---

