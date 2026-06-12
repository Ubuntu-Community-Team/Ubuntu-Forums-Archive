---
title: "Why oh Why???"
date: 2006-11-06
forum: General Help
---

### Post by unbreakable on 2006-11-06
Hey. lots of distos ask you what OS you want to load on default..
or at least have an easy way to change the default one...
But ubuntu (kubuntu) doesnt....

I want XP to be my default OS... but how do I change this?

any program that I can do this with a GUI and not a text editor?

thanks

---

### Post by Iarwain ben-adar on 2006-11-06
Hi,
just edit your /boot/grub/menu.lst file as root ;) 

> # You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0


Just edit the 0 with the number corresponding with the number Xp has (start counting from 0, and do +1 every time you see a mention of a "boot")

"boot": like these are 2 "boots" (everytime a "title" is mentioned ;) )
> title           Ubuntu, kernel 2.6.17-10-386
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-386 root=/dev/hdd1 ro quiet splash locale=nl_NL
initrd          /boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-386 (single-user mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-386 root=/dev/hdd1 ro single
initrd          /boot/initrd.img-2.6.17-10-386
boot



Hope that wasn't to difficult.


Iarwain

---

### Post by boban on 2006-11-06
```

sudo gedit /boot/grub/menu.lst 

```

There change "default		0" to something else... If you have 4 menu items (normal install):
- ubuntu
- ubuntu recovery
- memtest
- other OS (separator)
- Win Xp

You should change default to 4 (because counting starts from 0)

---

### Post by Iarwain ben-adar on 2006-11-06
> **boban said:**
> ```

sudo gedit /boot/grub/menu.lst 

```

There change "default		0" to something else... If you have 4 menu items (normal install):
- ubuntu
- ubuntu recovery
- memtest
- other OS (separator)
- Win Xp

You should change default to 4 (because counting starts from 0)

Read his post first ;)
Better explained :D


Iarwain

---

### Post by bollix47 on 2006-11-06
[Howto Change grub default.]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")

---

### Post by David Corrales on 2006-11-06
I recall there was a GUI utility to configure grub but I can't find it  =/
BUT, I can offer you a nice text editor and not a console one :)!
Type **gksudo gedit /boot/grub/menu.lst** to open the file, and then scroll down until you find a line that reads *## ## End Default Options ##*.
The OS entries start from that point, they're grouped by paragraph and should be counted from zero. That is, the second entry is 1, the third is 2, etc. Count up to the Windows XP one (usually the fifth one) and then scroll all the way up to the line that reads *default         0*. Change that number for the one you just found out remember to start counting from 0.

---

