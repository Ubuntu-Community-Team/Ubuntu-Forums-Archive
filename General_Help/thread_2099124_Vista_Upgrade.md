---
title: "Vista Upgrade?"
date: 2012-12-28
forum: General Help
---

### Post by JPR65 on 2012-12-28
So, Windows Vista is pretty  bad--and Windows 8 just came out. I've decided that I'd like to upgrade:

I dualbooted Ubuntu 12.04 and Windows Vista a while back on my main work computer (the partition sizes are about the same). Will upgrading Windows Vista (assuming that everything goes according to plan) at all effect the usability of Ubuntu 12.04? I heard about Microsofts "secure boot" feature, but I'm not sure if or how that will effect Ubuntu, especially since I've already succeeded in dualbooting the two OS's.

Supposing that something goes wrong, I've already made a backup, and am fully prepared for a failed upgrade; this is the only concern I have. 

Thanks!

---

### Post by irv on 2012-12-28
Remember if you upgrade Vista to Win 8 you won't be able to boot into Ubuntu. 
The right way to install any Windows and Ubuntu is to install Windows 8 and then Ubuntu. Windows will take the whole hard drive. So the right way to to this is to do a clean install doing Windows 8 first then Ubuntu. Yes, make sure you have all your personal files backed up so you can restore them when you are done.

---

### Post by JPR65 on 2012-12-28
Was hoping I wouldn't have to do that :(. Anyway, thanks for the input--I'll back up the few files I haven't already, do a clean install of Windows Vista, upgrade to Windows 8, then dualboot Ubuntu 12.10.

Thanks!

---

### Post by rrich1974 on 2012-12-28
in fact, by upgrade you mean a clean install of w8. but still, why dont you upgrade to w7 and wait at least for a service pack in W8....or maybe W9? 
w7 is pretty good and mature OS. now, let me tell you what i have done in W7 after installing. 
you can install an app named easyBCD and add a new entry in MBR of windows. you also must install the grub in ubuntu partition with the help of this app. 
look for some tutorials on youtube. easyBCD is a very usefull app. 
you dont need to format the entire hdd.

OFFTOPIC.
why dont you stick to vista, make full update and it will work great, it has support until 2017. you can use WISE CARE 365 as a tool for cleaning.

---

### Post by Primefalcon on 2012-12-28
you can install windows, then just reinstall the grub bootloader

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

here's an easy walkthrough

---

### Post by rrich1974 on 2012-12-28
lets face it man, it is much more easier by easyBCD in windows. 
i did this many times and never failed me.

---

### Post by JPR65 on 2012-12-28
Thanks everyone for the immediate support and great suggestions. It appears that I have some investigation to do :). 

To answer your question rrich1974, Vista is so slow that it is unusable, and yet Ubuntu runs so fast on my hardware. My PC is a quad-core 4gb ram with a pretty nice graphics card; I would expect it to run faster than on my slow laptop, and yet it doesn't. I would completely rid myself of Windows, except I need windows for several windows specific applications (rosetta stone, gaming etc. )

---

### Post by Primefalcon on 2012-12-28
if you have a look at the link I posted it actually has a graphical tool that repairs the grub bootloader.... pretty easy

---

### Post by irv on 2012-12-28
> **Primefalcon said:**
> you can install windows, then just reinstall the grub bootloader

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

here's an easy walkthrough

Thanks for the link: I put it in my Howto list.

---

### Post by JPR65 on 2012-12-28
I'm slightly confused now. So I upgrade to Windows 8 from Windows Vista (without reinstalling either OS). Then, Windows 8 will not overwrite the Ubuntu partition of the drive; instead it will just block access to it? Then I would apply one of the two methods that you guys suggested to recover access to the Ubuntu partition?

---

### Post by rrich1974 on 2012-12-28
if i would be in your shoes, i'd make a clean install of w8 on w vista partition. then, i will reinstall the grub.
i did that on w7, i dont know about w8. you should call to microsoft.

---

### Post by Mark Phelps on 2012-12-28
Sorry I don't have the link,but BEFORE you upgrade to Win8, you should run the Upgrade Advisor from MS to see what will upgrade and what will not.  Some Vista device drivers won't work in Win8, and vendors have been SLOW to come out with Win8 drivers -- shades of Vista all over again.

Also, unless (1) you have a touch screen (which most likely, you do NOT) or (2) you're a real fan of smartphone desktops and hate menus, I would advise strongly AGAINST upgrading to Win8 at this time.

You should consider upgrading to Win7 instead.

Your PC doesn't have the hardware needed to handle the Secure Boot offered by Win8, anyway.  So upgrading to that does nothing for you over Win7.

---

