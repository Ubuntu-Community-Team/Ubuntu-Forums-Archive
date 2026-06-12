---
title: "Vista, Ubuntu, Ubuntu in boot list?"
date: 2007-05-29
forum: General Help
---

### Post by Depressed Man on 2007-05-29
I finally got Ubuntu Feisty Fawn running at what I deem acceptable on my Sony VAIO laptop. I installed it with the help of Wubi. However, the first attempt was with a version of Wubi that didn't quite work with Vista so the Ubuntu install wouldn't work, so I tried another version found in a thread that dealt specifically with Vista. It worked :). However, now when I boot my laptop up it lists this..

Windows Vista
Ubuntu (the working one)
Ubuntu (the non working one)

However, the older (non working) Ubuntu install no longer exists. So how do I remove it from the list? I checked boot.ini in Windows but it just says

[operating systems]
c:\grldr="Ubuntu"
[boot loader]
timeout=15

Thanks! Oh, also should I summit my info to the laptop testing wiki? I don't think my specific VAIO model is listed there (I was checking earlier). But I'm not sure if the entry is valid if I use Wubi.

---

### Post by Crafty Kisses on 2007-05-30
You'd probably have to manually remove it.

---

### Post by Depressed Man on 2007-05-30
How? Do I edit grldr? Or is there some file like boot.ini?

---

### Post by ahaurw01 on 2007-05-30
If your compy uses GRUB to boot up then all you have to do is ```
sudo gedit /boot/grub/menu.lst 
``` and near the end of the file, comment out the listing of the OS that you don't want to show up.

If you happen to somehow use the windows booter, I'm sorry I can't be much help.

---

### Post by Depressed Man on 2007-05-30
Hmm it is the Windows boot loader, though I looked up how to edit it and found BCDedit. Though oddly it only shows the two OSes that work and not the defunct nonexisting Ubuntu install.. interesting.

Edit: Seems that fixed it even if I didn't have to delete anything.

Does anyone know the answer to my laptop question though? I'd love to help out.

---

### Post by Shadoweater12081980 on 2007-05-30
<rant> Firstly, Vista is HORRIBLE </rant>

anyhoo

boot to windows

start -> run
cmd
click ok

now in a dos prompt (assuming you are logged in as an administrative user)

attrib -r -a -s -h c:\boot.ini
copy c:\boot.ini c:\boot.old
edit c:\boot.ini

here is where your Windows boot selections are. You should see the 2 Ubuntu options, just delete the one you dont need. If all goes wrong you can always boot to a recovery CD and recreate the proper boot.ini from boot.old

Hope this helps

---

### Post by Depressed Man on 2007-05-30
Thanks, I did check boot.ini before but it wasn't there. It just has what I listed in my first post Apparantly Windows changed their boot process (foudn that out from googling and found the program BCDedit). The problem has been resolved though, thanks to everyone!

But I want to contribute what I learned about getting Feisty Fawn to run on my VAIO laptop to the laptop thread, but I'm unsure if my data would be valid due to my installation method of Linux.

Well, that and I'm trying to get the brightness controls working, as well as get hibernate/sleep (or what it's called in Linux..I forgot already) working since activating them seems to turn the comptuer screen off but apparantly my mute and numlock still work and I can't recover from it.

---

