---
title: "Adding isolinux.bin to Grub"
date: 2008-07-02
forum: General Help
---

### Post by shukababs on 2008-07-02
Hi all,

*I'm very new to Ubuntu/linux*

I'm very new here and I need to ask help regarding grub functionality.  I don't know if the question I will ask is possible.

There is a new project in the OSx86 (Boot-132) that would make you install Leopard using the Retail DVD.  I've actually tried it myself and it was great.  The only drawback of this setup up is that you have to boot from the BOOT-132 CD all the time to be able to boot to the installed Leopard drive.  I did not choose to install any fake EFI (like pc_efi or chameleon) because I want to make the BOOT-132 as my main booting option because of great advantages over the fake efis.  The thing is, I don't want to boot the CD everytime and I still want Grub (from my Ubuntu) to be the main bootloader.

I only have Ubuntu as my main OS and I'm planning to dual boot.
My setup:
1st HDD - Ubuntu 8.04
2nd HDD - my Leopard

I noticed that the BOOT-132 cd uses isolinux.bin when booting.  When I browse the CD, I see these files inside it:

isolinux.bin
boot
initrd.img
mboot.c32
isolinux folder > has isolinux.cfg inside

When I boot from the CD .. I see
kernel /boot
..Isolinux.bin 
initrd.img .....................................................

or something like that

Question:

Is there a way to copy the CD or ISO image of Boot132 and put it in my Ubuntu drive and just add an entry to my menu.lst so that I don't have to use the CD ever again?

Thank you very much.

---

### Post by ergosteur on 2008-09-19
try copying the contents of the cd to /boot/grub/osx/
then add something like this to your /boot/grub/menu.lst

title Mac OS X Leopard
root (hd0,x)
kernel /boot/osx/boot
initrd /boot/osx/initrd.img

where x is the number of your ubuntu partition (i think)

i'm not too clear on the usage of mboot.c32.

I'll try to do some tests myself... I used to have a triple boot using PC_EFI, and that worked fine but it seems this boot-132 method is more 'vanilla'.

---

### Post by maybeway36 on 2009-03-09
The isolinux.cfg has some settings that you might be able to change a little bit so they work in GRUB.

---

