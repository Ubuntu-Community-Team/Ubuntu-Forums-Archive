---
title: "really need some help if anyone can give it :( (yoga 11s)"
date: 2016-09-08
forum: General Help
---

### Post by mrharris2 on 2016-09-08
yes ive read its an arm processor and it shouldnt run other os but ive read a few posts too saying people have installed ubuntu flawlessly on it excluding the wifi driver.
my problem is when i upgraded to 8.1 (which apparantly was a big mistake) it encrypted my hard drive... which wouldnt be an issue... normally. so i was trying to stall an os (not ubuntu before i read that nothing else could be put on) and when id go into the uefi, and try booting from usb. the computer would completely ignore my usb... so i wanted to check the bios to see if maybe it had to do with the bios settings... but of course then bitlocker came up. I went to my microsoft acc and got the key and tried FIVE different times to unlock the encryption. the encryption says its off but the protection is on and of course if i try and go to uefi..... needs key that says its unlocked but loops asking me to unlock again and again and if i try from the manage bde protection off it says the functions not available on 8.1 x.x

needless to say it never happened and ive been stuck on 8.1 because even if i go into a admin cmd and try to remove protection it will way the current os does not work with it and to install a different os... so great now i cant even mess with the drive at all... least thats how it feels...

i tried seeing if there was a way to force wipe the os while i was on it.. hoping it could maybe let me get into the bios (probably not a good idea in the first place even if i can do it) but since im on it, it says its not possible because its in use.....
ive wiped this laptop long since after the 8.1 upgrade and it still leaves 8.1 on it so... can anyone please help me? i just want any os regardless of what it is BESIDES rt if any (which is why i was hoping cause ive seen posts about ubuntu for 11s) to lift these stupid restrictions on the laptop.

by the way, yes in the beginning i did read up on its limits when i bought it but originally it was a gift to my mother because her old laptop died and she only used this for facebook and youtube. now she has a bigger laptop and i was trying to make use of this laptop but the speed on it as far as trying to play anime and youtube is cringe worthy as it constantly freezes every 2 seconds during play :(
so if anyone can please help me get around this bitlocker issue and maybe help me get ubuntu or anything else besides rt... youd be a godsend to me.
edit:if i do manage to get it to work... does it have to be a specific lubuntu version to work? i had just tested the usb i made by accident and it loaded just fine on the computer i shut down and ran this morning. but again, the yoga ignores it

---

### Post by grahammechanical on 2016-09-08
> [COLOR=#333333][FONT=Ubuntu]yes ive read its an arm processor ... [COLOR=#333333][FONT=Ubuntu]does it have to be a specific lubuntu version to work? [/FONT][/COLOR][/FONT][/COLOR]

It would have to be an OS that runs on ARM CPUs. I am not sure if there is a Lubuntu version that runs on ARM. There are Ubuntu versions for a few ARM processors but they tend to be server images.

[http://cdimage.ubuntu.com/ubuntu/releases/16.04.1/release/](http://cdimage.ubuntu.com/ubuntu/releases/16.04.1/release/)
> 
[h=3]mini system in UEFI mode[/h] While  the minimal iso image is handy, it isn't useful for installing on  UEFI-based systems that you want to run in UEFI mode. The mini iso lacks  the proper files for booting the computer in UEFI mode. Thus, the  computer will boot in BIOS compatibility mode, and the installation will  be in BIOS mode. 

You can use an **Ubuntu Server amd64 iso file** (64-bit) for 'mini installations' in UEFI mode. There is a compressed image file **dd_text_16.04-UEFI-n-BIOS-4-pendrive-7.8GB.img.xz** of such an installed system, that can be used as a start of a custom installation. 

See this link: [Installation/UEFI-and-BIOS/stable-alternative]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative").

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

With a server edition or the Mini ISO image in BIOS/Legacy mode you choose which desktop you want. At the basic level the server or Mini ISO will give you a Linux command line installation to which we add the desktop environments and user interfaces of our choice and then add programs.

Regards.

---

### Post by mrharris2 on 2016-09-08
> **grahammechanical said:**
> It would have to be an OS that runs on ARM CPUs. I am not sure if there is a Lubuntu version that runs on ARM. There are Ubuntu versions for a few ARM processors but they tend to be server images.

[http://cdimage.ubuntu.com/ubuntu/releases/16.04.1/release/](http://cdimage.ubuntu.com/ubuntu/releases/16.04.1/release/)


[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

With a server edition or the Mini ISO image in BIOS/Legacy mode you choose which desktop you want. At the basic level the server or Mini ISO will give you a Linux command line installation to which we add the desktop environments and user interfaces of our choice and then add programs.

Regards.

does it matter using a x64 mini if the arm is x32? and my problem is the 11s ignores the usb regardless of what i put on it and you cant get into the bios settings cause of bitlocker and even if you enter the correct bit key, itll say success but instead of proceeding to the advanced options, itll instead load the computer like you didnt request anything at all :/

---

