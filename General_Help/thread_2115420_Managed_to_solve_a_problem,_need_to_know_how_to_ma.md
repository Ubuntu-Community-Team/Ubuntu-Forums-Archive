---
title: "Managed to solve a problem, need to know how to make it standard"
date: 2013-02-12
forum: General Help
---

### Post by Mantinziza on 2013-02-12
Ok, ive been fighting with getting an nvidia card working which I finally did :D  when i went into the grub menu apprently all i had to do was remove quitsplash replace with nomodest... yadada.  How do I set this up so I don't have to do this every time.    I am still new even though i got this to work, so simpple terms please. And thank you. I'm excited :)  its 12.04 btw

---

### Post by matt_symes on 2013-02-12
Hi

You need to edit the file /etc/default/grub.

```
sudo nano /etc/default/grub
```Look for the line that says

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and add the nomodeset parameter to it. 

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

Save the file....

Ctrl + o then ctrl +  x.

...and then type

```
sudo update-grub
```Kind regards

---

### Post by ibjsb4 on 2013-02-12
Did you go to the file /etc/default/grub and change it there?  And if so did you ..

```
sudo update-grub
```

After you made the change?

If you did, thats all you needed to do and your good to go.

---

### Post by Mantinziza on 2013-02-13
this is all well and good, but where do I type that code in. Im looking at the (press e at the grub menu part), part. And im not seeing a file/sudu/... thing youre talking about.

 Im lucky i even got it working.   I need more details please. and thankyou   This here is exactly what im seeing on my screen right now. and how i switched to nomodeset in the first place.

 -------------------------------------------------------------

 setparams 'Ubuntu, with linux 3.2.0-37-generic-pae'  record fail gfxmode 

$linux_gfx_mode insmode gzio insmod part_msdos insmod ext2 set 

root+'(hd1,msdos7) ' 

search --no-floppy --fs-uuid- --set=root 2ff5b32a-4e71-4f27-b33a-ddfc22a7d792 linux 

/boot/vmlinuz-3.2.0-37-generic-pae root=UUID=2ffb352a-4e71-4f27-

b338-ddfc22a7d792 ro  _quiet splash_ $vt_handoff

initrd /boot/initrd.img-3.2.0-37-generic-pae

------------------------------------------------------------

The underlined quietsplash in that code is what I changed to nomodest to get it finally working. Now it is working but it's getting annoying doing this everytime on startup.

HOw do i fix this, and please tell me step by step how to do this. The parts you guys listed above ARE NOT any where on this section. 

I am new to this, please help me.

---

### Post by schragge on 2013-02-13
You type it in a terminal window **after** you booted into Ubuntu, not before.

---

### Post by ibjsb4 on 2013-02-13
You need to do what matt said in post #2.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo gedit /etc/default/grub
```

That will open up your editor.

And like schragge said, you need to boot into Ubuntu and not the grub menu to do this.

If you need further instruction, please post back.

---

### Post by grahammechanical on 2013-02-13
Are you sure that the problem is fixed?

Adding nomodeset to the boot parameters as you have done only loads Ubuntu without it trying to detect a monitor video mode and getting the setting wrong for some reason.

Once we have got to a desktop we usually need to go into Additional Drivers and activate a driver. The Additional Drivers utiltiy should give you a choice of Nouveau (open source) and several Nvidia proprietary drivers even experimental ones.

Regards.

---

