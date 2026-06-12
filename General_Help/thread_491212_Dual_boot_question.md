---
title: "Dual boot question"
date: 2007-07-03
forum: General Help
---

### Post by rmbr3and28 on 2007-07-03
I have successfully installed Ubuntu 6.10 on the second hard drive of my windows XP media center PC so I can decide if I want to keep it. On booting up Ubuntu is the default choice and I am asking how do I make my windows os the default choice. Any suggestions would be greatly appreciated.

---

### Post by rajmilton on 2007-07-03
Just edit /boot/grub/menu.lst.  This is the config file that GRUB uses to display the multiline os selection screen at boot time. Just search for the following lines (more or less similar):
   title Windows XP media center
   root (hd0,0)
   savedefault
   chainloader +1

Move these set of lines just above the following set of lines
   title Ubuntu 6.10
   root (hd1,0)
   kernel /boot/vmlinuzxxx root=/dev/hdb1 ro quiet splash
   initrd /boot/initrdxxx
   savedefault
   boot

---

### Post by mikewhatever on 2007-07-03
Count the lines in the grub menu you see at boot, if you do not see the menu, hit Esq, and write down the number for Windows. Now boot into Ubuntu, go to Applications>Accessories>Terminal copy the following command and press Enter.
> gksudo gedit /boot/grub/menu.lst
After typing in your password, you'll see the following
> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
[COLOR="Red"]default		0[/COLOR]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
Change the 0 (zero) in [COLOR="Red"]default 0[/COLOR] to the number you got for Windows minus 1 (if the number is 6, type 5), save end exit.

---

### Post by mikewhatever on 2007-07-03
Rajmilton, an entry of Windows will be deleted from the debian kernels section every time the kernel is updated.

---

### Post by rmbr3and28 on 2007-07-04
Thanks so much.

---

