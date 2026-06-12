---
title: "Dual Boot Question"
date: 2007-03-20
forum: General Help
---

### Post by CheeseQueen452 on 2007-03-20
My mom is trying Ubuntu on a dual boot system with win xp. When the boot manager appears, there are 4 entries for Ubuntu. 2 for kernel 2.6.20-11, & 2 for kernel 2.6.20-10. One of each version is a safe mode option. Somewhere on these forums I read about removing the extra entries from the menu.lst file. Is it really safe to do this? I don't want to cause any problems on her computer! Oh, & do you have to log in as root to edit the file?

---

### Post by EtrnlApocaplypse on 2007-03-20
It's perfectly safe to do this....i would keep the "safe" mode entry for the one you keep and obviously make sure you keep the working one. You don't need to log in as root in fact you should almost never, in fact don't ever log in as root. That is what the sudo command is for. Just make sure you use sudo to launch whatever editor you are going to edit the file in. This command gives root privileges.

---

### Post by gepatino on 2007-03-20
The best way to remove old kernel images is using synaptic.

If you edit menu.lst to remove the entries, the kernel images will still be installed. Go to sypantic, search for linux-image, and delete the old versions. 

(be carefull, and be sure you are leaving at least one working image installed)

---

### Post by CheeseQueen452 on 2007-03-20
Thanx, guys.... My mom says the multiple entries don't bother her, so we'll just leave it alone. If it ain't broke, don't fix it.....

---

### Post by IcemanV9 on 2007-03-20
@CheeseQueen452 - your mom's menu list is perfect. One primary kernel (2.6.20-11) with safe mode option and one backup kernel (2.6.20-10) with safe mode option.

However, you can change the look a bit, such as, 

[LIST=1]
[*]limit kernel to 2 or 3 in the list

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
```

[*]hide the list until press 'ESC' to see the menu

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

[*]OR, remove the kernel image (just like gepatino said earlier) and menu.lst will be updated automatically.

```
sudo aptitude remove linux-image-2.6.xx-xx
```
[/list]

There is a very good [[COLOR="Orange"]**wiki**[/COLOR]]("https://help.ubuntu.com/community/GrubHowto") on grub.

Word of caution: please make a backup copy of menu.lst before you modify it. :)

---

