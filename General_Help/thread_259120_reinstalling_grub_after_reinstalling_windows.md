---
title: "reinstalling grub after reinstalling windows"
date: 2006-09-16
forum: General Help
---

### Post by Polygon on 2006-09-16
im in the process of reinstalling windows (yes i know, wonderful windows. I have to reinstall because windows freezes every time i want to open "my computer" -.-)

anway i know that reinstalling windows will wipe out grub, how do i reinstall it via a live cd? there was some command to do it with the terminal or something

and please dont tell me to do the way where you go through the process of reinstalling ubuntu only just reinstall grub. that never works and just screws up my partiton table

thanks

---

### Post by catlett on 2006-09-16
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by Polygon on 2006-09-16
thats exactly what i need, but one question, will grub automatically search for other operating system and add them to my grub.lst, or will i have to do this manually

(as in, will reinstalling grub make me unable to boot into windows?)

---

### Post by catlett on 2006-09-16
Whatever is on your list before you install windows will be there after you run the live cd setup of grub. Grub is going to find and use your ubuntu menu file. So, if you have windows as an option now, it will be there after you reinstall. If for some reason, it doesn't have windows, you can add it.
To be safe, make a copy of your grub menu and save it somewhere, you can even post it here as a reply and archive it that way.
When you get back into ubuntu, open the grub menu with```
 sudo gedit /boot/grub/menu.lst
``` and add the entry for windows. I doubt you will have to do this but it is better to have a copy and backup plan and not need it then to need it and not have it. 
Anyways, you should be fine. Every time I ran it, it used the same menu that was on the OS before.

---

### Post by Polygon on 2006-09-17
thanks. I had a rough time, because find /boot/grub/stage1 didnt do anything for me, but i managed to get the boot partion of my ubuntu drive mounted and i looked at the menu.lst file to see what partiton (hd1,0) ubuntu was installed on, and then i used that value and it worked. thanks

---

### Post by 23tv on 2007-10-20
HI, i just reinstalled my GRUB by following your instruction and now when im at the dual-boot menu, i try to run windows but it gives me this error

"error 12: invalid device requested" 

how to solve this??

---

### Post by meierfra on 2007-10-20
post the output of

```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```

---

### Post by stinkinrich88 on 2007-10-20
dude, it's ALL about supergrub: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) 

live CD, bit complex to use but you'll figure it out. Works a treat.

---

### Post by meierfra on 2007-10-20
Based on your information in your other thread:

Open menu.lst via

```
gksudo gedit /boot/grub/menu.lst  
```

and change > title Microsoft Windows XP Professional
root (hd0,0)

to
> title Microsoft Windows XP Professional
root (hd0,3)

---

### Post by Duck2006 on 2007-10-20
> **meierfra said:**
> Based on your information in your other thread:

Open menu.lst via

```
gksudo gedit /boot/grub/menu.lst  
```

and change 

to

he will also have to remap the drive so windoze see it sleft as (hd0,0)

---

### Post by meierfra on 2007-10-20
> he will also have to remap the drive so windoze see it sleft as (hd0,0)

You only need "map"  if windows is not on the first hard drive. You don't need it if windows is on the first drive but not on the first partition.

---

