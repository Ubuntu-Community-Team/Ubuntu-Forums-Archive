---
title: "Grub modify help"
date: 2008-06-05
forum: General Help
---

### Post by wengkhin on 2008-06-05
........................

---

### Post by iaculallad on 2008-06-05
> **wengkhin said:**
> Did anyone have any code or cmd that will make windows xp pro to be shown at first then ubuntu in the dual boot selection(grub)I still didnt install ubuntu yet because i am not sure of it.TY:confused:

You could try interchanging menu list in your GRUB menu (windoze settings first then your Ubuntu), GRUB menu is located here: /boot/grub/menu.lst

---

### Post by arsenic23 on 2008-06-05
All you have to do is edit the file [COLOR="DimGray"]/boot/grub/menu.list[/COLOR] to have the windows entry above the ubuntu ones.

---

### Post by leito666 on 2008-06-05
After Ubuntu install, go to console and install

```
sudo apt-get install startupmanager
```

That program will help you to set grub options.

---

### Post by tamoneya on 2008-06-05
just edit /boot/grub/menu.lst.  You will see the boot options near the bottom.  Also look for the variable "default" it tells grub which OS to boot.  eg: if this is the order of your OS at the bottom of menu.lst```
ubuntu
ubuntu recovery
windows xp
```then you should set default to 2 because it is zero based index.
To edit this you need to have root permissions:```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by drs305 on 2008-06-05
arsenic23 is correct in that you can physically move the order around in menu.lst. However, as both the other posters mentioned, there are other ways to do this.

I suggest you read the following. I wrote it yesterday and explains all your options:

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by wengkhin on 2008-06-05
-----------------------------

---

### Post by drs305 on 2008-06-05
> **wengkhin said:**
> Sorry for interrupt can u show me how to modify the boot option step by step follow by windows xp then ubuntu.TY

It would be safer to make the default windows xp without physically moving the entries in the menu.lst. You can do this by editing menu.lst or via startupmanager. The link I provided in post #6 should answer your questions on how to do this. 

We will be glad to help if they don't. ;-)

---

### Post by confused57 on 2008-06-05
This should help also:
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

The link drs305 explains it very well, but basically to edit your menu.lst you'll need to open a terminal(Applications---Accessories---Terminal):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

---

### Post by Ptero-4 on 2008-06-06
You can open the /boot/grub/menu.lst (it's a lowercase L) file and put the Windoze entry above the portion marked as "automagic".

---

