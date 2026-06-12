---
title: "How do you remove grub from a partition?"
date: 2006-10-19
forum: General Help
---

### Post by jimisdead on 2006-10-19
Hi, i just messed up big time - I reinstalled windows xp (dual-boot machine) and of course had to reinstall grub. So I boot from the (k)ubuntu install cd, mount my dapper partition (sda6) on /ubuntu , and run

sudo /sbin/grub-install --root-directory=/ubuntu /dev/sda**6**

when I should have run

sudo /sbin/grub-install --root-directory=/ubuntu /dev/sda

and now my machine kernel panics when I boot - at the 'mounting root' part.

Does anyone know how to remove/uninstall grub from a partition? Or otherwise know how to fix this problem? I have a heap of uni work due tomorrow and reinstalling the entire system will no be good for my assignment.

Thanks.

---

### Post by CatKiller on 2006-10-19
You should be OK just installing GRUB to the right place. I'm confused as to why you're using --root-directory=/ubuntu - won't that make it use /ubuntu/boot/grub rather than the usual /boot/grub? I don't know that much about GRUB, though, so perhaps you know what you're doing.

You don't get rid of GRUB without replacing it with something else, but AFAIK, if it isn't explicitly called, it's not a problem. If it remains a problem after you've set GRUB up properly then there is a risky procedure that you can use to replace wherever you've put GRUB on sda6 with zeros.

---

### Post by Lin-X on 2006-10-19
Well, maybe you could just boot from a Windows boot floppy and then type
fdisk/mbr. This, at least would get you back to where you started.

---

### Post by Lin-X on 2006-10-19
I appologize if the preceeding post seemed stupid or not related to your problem. I have many distractions at this moment. I will log on again later and see if you have solved your problem. PLEASE POST AGAIN IF YOU HAVE. If not, I will try to help you. Sorry I can't be of more immediate use!

---

### Post by jimisdead on 2006-10-20
At the moment grub is properly installed into the MBR pointing to sda6 as the location of the menu file, so when I boot it brings up the menu and I am able to choose linux or windows... 

if I choose windows, it boots fine, but if I choose linux and it attempts to boot from sda6 then it gets a kernel panic when trying to mount the root filesystem... something along the lines of 'tried to read past the end'. The only thing out of the ordinary that has happened to the sda6 partition was my mistake when reinstalling grub.

(when reinstalling grub you need --root-directory=/ubuntu because when booting from the live CD root is the *CD* root, and /ubuntu is the root of the filesystem I want to boot from, ie sda6)

---

### Post by CatKiller on 2006-10-20
> **jimisdead said:**
> (when reinstalling grub you need --root-directory=/ubuntu because when booting from the live CD root is the *CD* root, and /ubuntu is the root of the filesystem I want to boot from, ie sda6)

I see. Thank you. I've only ever used **grub** rather than **grub-install**, so I didn't know how that worked. I guess there is something wrong with that partition then, but it's more than I'd know how to fix, as you've probably gathered. Hopefully someone better will be able to help you.

---

### Post by jimisdead on 2006-10-20
Thankyou to everyone who read... unfortunately I have run out of time to fix this and will need to do a reinstall now or I will not have time to finish my assignment... if learn of a way to fix this in the future I will post... cheers.

---

