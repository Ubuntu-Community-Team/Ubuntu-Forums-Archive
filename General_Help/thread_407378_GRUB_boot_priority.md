---
title: "GRUB boot priority"
date: 2007-04-12
forum: General Help
---

### Post by GexX2 on 2007-04-12
I'm new to Linux, and I see I have a new boot loader :P While grub is nice, I want to change the order the OS's are listed, as Windows is still my primary OS. Now they are, (shortened of course)

----------------------------
Dapper 28
Dapper 28 recovery
Dapper 26
Dapper 26 recovery
--others--
Windows XP
---------------------------

I have no clue why theres 2 Ubuntu Dapper installs (28 and 26) but I'd hoped you could explain that one as well.

But what I want Grub to look like is

----------------------------
Windows XP
--others--
Dapper 28
Dapper 28 recovery
Dapper 26
Dapper 26 recovery
---------------------------

Does anyone know how to go about doing that?

---

### Post by dcstar on 2007-04-12
> **GexX2 said:**
> I'm new to Linux, and I see I have a new boot loader :P While grub is nice, I want to change the order the OS's are listed, as Windows is still my primary OS. Now they are, (shortened of course)

----------------------------
Dapper 28
Dapper 28 recovery
Dapper 26
Dapper 26 recovery
--others--
Windows XP
---------------------------

I have no clue why theres 2 Ubuntu Dapper installs (28 and 26) but I'd hoped you could explain that one as well.

But what I want Grub to look like is

----------------------------
Windows XP
--others--
Dapper 28
Dapper 28 recovery
Dapper 26
Dapper 26 recovery
---------------------------

Does anyone know how to go about doing that?

You have 2 Dapper kernels installed, you may want to remove the 26 one (use Synaptic).

It may be difficult to move Windows to the top of the list as every time you get a Kernel upgrade it will re-write that part of the Grub menu.

Change the Grub "Default" option to the right number (0 through X depending on how many items in you menu) if you want to have your Windows selected by default.

---

### Post by ramjet_1953 on 2007-04-12
Hi, there!

What you want is quite easy, but you need to be sure that you are accurate.

The file that you need to edit is [COLOR="Blue"]/boot/grub/menu.lst[/COLOR]

Before editing this file, you need to make a copy of it first and give it a different name [COLOR="Blue"]menu.lst.bak[/COLOR] would be OK.

You can only edit this file in super user mode, so you would type:

Code:

[COLOR="Red"]gksu gedit /boot/grub/menu.lst[/COLOR]

It will then ask for your administrator password and after you enter it, the file will open in an editor.

If you have a look, the top of the file has examples of how you can set-up GRUB, but as you scroll down, you will see lines without a [COLOR="Blue"]#[/COLOR] at the start of the line. These are the working entries.

You will notice that all of your current boot options are there.

All you now have to do to get them into the order that you want is to CAREFULLY cut and paste the entries into the order that you want.

When you have TRIPLE CHECKED that all is OK, just save the file and re-boot.

If you did it right the boot order will be what you wanted.

If you stuffed-up horribly, in a terminal, just re-name the original file that you backed-up to menu.lst

Regards,
Roger :cool:

---

### Post by GexX2 on 2007-04-13
Thanks for the help. I was searching through the forums, and found someone with a link to a Grub boot loader page in thier sig, and it helped alot. Got it set up just like I wanted :3 Even hid my unused kernels, and added a splash screen :3 Thanks again!

---

### Post by cozadaman on 2007-12-17
An easier way that cutting and pasting your boot entries is to just change your default boot.
so this is starting from 0 and the "other operating systems counts as a number so 1 kernel = 0, 1 recovery mode = 1, 1 mem test = 2, 1 other operating system title = 3 and 1 other operating system = 4.


You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		4

So 4 for me would boot other operating system. you just have to change the one number.

---

