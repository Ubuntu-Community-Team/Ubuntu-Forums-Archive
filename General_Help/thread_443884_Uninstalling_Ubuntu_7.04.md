---
title: "Uninstalling Ubuntu 7.04"
date: 2007-05-14
forum: General Help
---

### Post by frediship on 2007-05-14
Hi guys, unfortunately I need to un-install ubuntu and re-install windows, The only problem is im a complete noob and have read and re read the guide ([http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)) and still cant make any sense of it. I have managed to partition the disk! but have not managed to get any further. 

so this is what i have:
*HP ZD7000 laptop 
*windows disk labeled: Windows XP service pack2 
*no floppy drive 
* and i am not dual booting 
* GParted live cd

any help would be appreciated.

---

### Post by earobinson on 2007-05-14
assuming you want to fully wipe ubuntu the windows cd will do this for you.

Sorry to see you go, you can still use open source software with windows, gaim, open office, firfox, gimp all have windows ports.

---

### Post by rsambuca on 2007-05-14
If you are just going to go with Windows, you don't actually need to uninstall anything.  You can have Windows overwrite the existing disc drive.  If you just put the XP disk in the drive and boot from the CD you should be able to just follow along with the Windows installer.

The only problem I can think you might have is that the XP installer doesn't recognize the drive for some reason or another.  If that is the case use the gParted CD you have and format the drive as ntfs, and then restart from the XP disk.

---

### Post by m.musashi on 2007-05-14
So you have a laptop with just Ubuntu and you want to replace it with XP? If you don't care about loosing Ubuntu or anything else you can just install XP as you would any other time. It will wipe Ubuntu out and you will have XP. However, if you have multiple partitions, XP will only install to the first one (I think). I can't remember exactly, but I don't think the XP CD has any tools for managing partitions. You will need to use something like gparted from a live CD and delete all partitions. Then windows will install using the whole drive.

Does that sound like what you want to do?

EDIT: oops, too slow.

---

### Post by frediship on 2007-05-14
i will miss it........ When i boot to the cd i have, nothing happens, it simply restarts ubuntu. I have no clue how to get it into recovery mode or whatever. Do i have the right disk?

---

### Post by m.musashi on 2007-05-14
Ah, I think maybe you don't have your CD drive set to boot before your HD. Go into your BIOS and change the boot order to CD first.

---

### Post by rsambuca on 2007-05-14
You will need to change the boot order on your computer's Bios.  To enter the bios, you usually have to hit a key shortly after turning it on.  On some machines it is Esc, some it is F12, you will have to try them or check with your manual to find out.

Once in the bios, there is a section that allows you to set the boot order.  Put your CD drive first, save, and reboot.

EDIT:  Oh, musashi got me this time!

---

### Post by frediship on 2007-05-14
ok thank you i will double check that and post back when i do.

---

### Post by earobinson on 2007-05-14
perfect.

---

### Post by frediship on 2007-05-14
yes, i am booting to the cd drive.

---

### Post by m.musashi on 2007-05-14
You're booting the CD and everything is okay? Or you are booting the Cd and it isn't working? Hopefully the former.

---

### Post by frediship on 2007-05-14
haha i wish, no i am booting to the cd drive and nothing is happening it goes straight into the GRUB thingy.

---

### Post by Espreon on 2007-05-14
I am curious why do you need to put Windows back on your comp?
Seriously why are you losing your Linux Angel wings and falling into Windows hell again?

---

### Post by MontanaMax on 2007-05-14
If the only Windows CD you have says "Service Pack 2" then you don't actually have the right CD to install from. You need the "Windows XP Installation Disk" to do the main installation from, and then when that is complete insert the "Service Pack 2" cd to put the service pack on that will fix a few hundred bugs in the base XP system.

Good luck!

---

### Post by frediship on 2007-05-14
Thank you max i had a hunch!
haha yeah Ubuntu doesn't have any "steller" video production software, which i need for my film class.

---

### Post by Espreon on 2007-05-14
Havent ya heard of Wine or CrossOver Linux so you could have yer "stellar video production software: run on Ubuntu?

---

### Post by frediship on 2007-05-14
im so gay

---

### Post by m.musashi on 2007-05-14
> **frediship said:**
> Thank you max i had a hunch!
haha yeah Ubuntu doesn't have any "steller" video production software, which i need for my film class.

There is also [Cinelerra](http://heroinewarrior.com/cinelerra.php3), but I hear it is rather intense and geared for professionals - maybe just what you are looking for.

---

### Post by frediship on 2007-05-14
hahaha, that is such a perfect program...... only if i saw that 2 hours ago
i might just have to re install ubuntu........

thanks for all you help.

---

### Post by m.musashi on 2007-05-14
Actually, if you want to go that route, you might want to check out [Ubuntu Studio](http://ubuntustudio.org/). It's a custom Ubuntu distribution geared toward multi-media users. I think the first version is heavy on audio but you can probably add Cinelerra and it may have some other tools that you find useful.

---

