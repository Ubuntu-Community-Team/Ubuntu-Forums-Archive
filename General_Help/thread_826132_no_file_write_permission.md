---
title: "no file write permission"
date: 2008-06-11
forum: General Help
---

### Post by ronti69 on 2008-06-11
Hello,
I am trying to edit the file menu.lst in the bootloader Grub and always get this message:

Warning: unknown mime-type for "/root/grub/menu.lst" -- using "application/*"
Error: no write permission for file "/root/grub/menu.lst"

I tried using "su" but that didn't change anything.

Sorry, this might be a very stupid question since my experience with Linux is only about 2 days...

Can someone please point me in the right direction?

Thanks

---

### Post by cariboo on 2008-06-11
The way to do it:

In a terminal (located in Applications-->Accressories-->Terminal) type:

```
sudo gedit /boot/grub/menu.lst
```

It might be a good idea to make a backup copy first.

Jim

---

### Post by sisco311 on 2008-06-11
Try:
```
gksu gedit /boot/grub/menu.lst
```from a terminal.

gksu - edit the file as root.
gedit - default text editor in gnome
/boot/grub/menu.lst - the location of the file.

Before you edit the file create a backup:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by drs305 on 2008-06-11
Note:menu.lst is in /boot/grub/menu.lst

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak1
gksudo gedit /boot/grub/menu.lst
```

However, I strongly recommend changing menu.lst with StartUp-Manager.
Go to System > Administration > StartUp-Manager> 

If you don't have it on your menus, install it with:
```
sudo aptitude install startupmanager
```

For more information on StartUp-Manager and boot displays, please take a look at:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by todak on 2008-06-11
Hello ronti69. Welcome to Linux in general, Ubuntu specifically.
 the "su" command is not used by default in Ubuntu. "sudo" is the command issued to become root ("administrator" is the equivalent in Windows) temporarily. To edit menu.list go to Applications > Accessories > Terminal. When terminal is running, type in the following ```
sudo gedit /boot/grub/menu.lst
``` sudo is temporary root to give you write permissions for system files, gedit is the gnome text editor, and /boot/grub/menu.lst is the heirarchial location of the file you wish to edit. Hope this helps :)

---

### Post by ronti69 on 2008-06-11
Thank you all. As you can see I am very new to linux... but laready loving it.
You rock, thanks again

---

