---
title: "Vista Home Premium and Ubuntu Edgy Eft with SATA"
date: 2007-02-20
forum: General Help
---

### Post by brokencrystal on 2007-02-20
I have a Dell Inspiron 1501 notebook and when I would try to install Ubuntu Edgy, it would error out every time I tried to load the boot CD. It would never boot. It would just give me a soft CPU lock error. I found that there is an error where if you have an SD card in the built-in slot, it will do this every single time. I think the problem is with Linux, because Windows Vista has absolutely no problems with this. Anyway...

Now I wanted to dual boot Vista and Ubuntu Edgy. (I have dual booted XP and Ubuntu Edgy many times before on other computers)  I first installed a clean install of Vista. I then removed the SD card. Then I booted the Ubuntu Live CD. I had to use option pci=nomsi to install it as it has a 2.5" laptop SATA drive. I adjusted the size of my Windows partition. Everything went perfect except, in the grub boot menu, it will not allow me to boot Vista now. Maybe because Vista is new and grub doesn't know how to handle it? Ubuntu boots fine. I tried to edit the /boot/grub/menu.lst to get Vista to boot from the SATA drive, but I had no luck. (Maybe I am not doing it correctly) I uncommented the part of the file that refers to booting Windows, and now I see it in the boot menu and can try to boot to it, but now it comes up with the error: NTBLDR not found or something like that... Forgot now as I just installed Vista back on it.

Has anyone ever done this before? Does anyone know how to do such a thing? Thanks in advance!

---

### Post by setinstone31 on 2007-02-20
dude you better hurry up and reinstall vista or their week per key will expire!

---

### Post by Nectron on 2007-02-20
You're gonna have to reinstall Windows Vista and adjust its partition size. Vista gets messed up when you resize its partition. 

Remove everything, install windows vista and make sure you leave the proper "unallocated" space for Ubuntu. Once you're done installing vista, start installing Ubuntu and when you get to the partitioning part "DO NOT RESIZE VISTA'S PARTITION"!! Install Ubuntu on the unallocated space.

When you're done, you're gonna have to edit the GRUB menu to add Windows Vista to it.

Follow the steps:
1.Open Terminal and type the following at the prompt:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
```
and enter your root password when asked,

2. Type ```
sudo gedit /boot/grub/menu.lst[code]
This will bring up the GRUB menu file.

3. Look for the line ## ## End Default Options ##, and directly under that, type:
[code]
title Windows Vista

root (hd0,0)

makeactive

chainloader +1

```

Then press Save..

A resized Vista partition will not make vista load, even if you add the vista entry to GRUB. Vista will only display the loading screen but will just sit there.

Hope this solves your problem, it solved mine yesterday :)

---

### Post by jimbob on 2007-02-20
XP works OK when you resize its partition.

Do you suppose that M$ did this on purpose in Vista to throw another roadblock in us dual-booters path?

Nah - they wouldn't do that ...
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by brokencrystal on 2007-03-02
This worked perfectly.  Thanks

---

### Post by Athanasius on 2007-03-02
I have the same laptop but the live disk is not finding the unallocated space.. it doesn't find a hard disk at all.  I hate microsoft

---

