---
title: "[SOLVED] Grub Stage 1.5 Error 5"
date: 2008-01-17
forum: General Help
---

### Post by DillyP on 2008-01-17
I have a HP dv9000 that had Vista preinstalled.  I installed Gutsy on the second hard drive.  I have been having all kinds of trouble with grub.  

Occasionally upon reboot or powering on Grub will stop at Stage1.5 and give me an error 5.  From what I can tell this happens everytime I reboot from anything except the Ubuntu install or the live CD (ie Windows or making any changes to the Bios)  

The only way I can get around this is to boot onto the live CD, wait until the drive that the ubuntu install is on mounts ( I usually have to click Places-->Computer then double click on the drive), and then reboot.  Then I am able to boot into Ubuntu or Windows.  Doesn't make any sense to me.  

Anyone have any idea how I can get grub to load reliably?

---

### Post by logos34 on 2008-01-17
You could try instead using Vista ([EasyBCD]("http://neosmart.net/wiki/display/EBCD/linux")) to load ubuntu

---

### Post by DillyP on 2008-01-17
I have installed that before, was never able to get my Ubuntu install to load.  That said, at this point I'd be willing to give it another go.  I'm just wondering if that will add to the complexity of it... if I remember right EasyBCD takes the place of BOOTMGR for vista... but it doesnt replace grub, EasyBCD just hands off the boot process to grub when you select the Ubuntu entry doesn't it?

---

### Post by DillyP on 2008-01-17
Installed EasyBCD again, but grub still tries to load before EasyBCD does.  More importantly, I might have solved the grub problem simply by unplugging my external hard drives.... seems to work great since I have... booted in and out of Vista 3-4 times.  Just for future reference if any body reads this and knows why EasyBCD wont load before grub will, what I can do to fix that... I'd sure like to know!

---

### Post by Computer Guru on 2008-01-18
Simply instaling EasyBCD is not enough. You need to select "Reinstall Vista bootloader" in the "Bootloader Management" page.

---

### Post by DillyP on 2008-01-18
Much better, thanks!

---

### Post by Computer Guru on 2008-01-18
You're welcome, glad it's working now.

---

