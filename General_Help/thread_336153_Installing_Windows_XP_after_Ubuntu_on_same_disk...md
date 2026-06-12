---
title: "Installing Windows XP after Ubuntu on same disk.."
date: 2007-01-11
forum: General Help
---

### Post by gejr on 2007-01-11
Hey..

I will soon have to install WinXP on my computer in addition to Ubuntu because of my need to use a statistics program called SPSS. I'm afraid of messing up grub and not get back into Ubuntu, since this is where I will keep all my impotant stuff.

A) How will I partition my harddisk? As of now I have it partitioned something like this:
    1 gb for swap
    10 gb for /
    ~30 gb for /home

B) How can I take 5-10 gb off of the /home partition to install windows without messing up the grub?

Thanks for reading!

---

### Post by anaconda on 2007-01-11
You should be able to resize your home-partition for-example with qparted (or was it gparted?)and installing winblows to the free space. Boot with ubuntu install cd and run the qparted from there. Then before you install windows you should learn how to reisntall grub-bootloader because windows installer will overwrite you old bootloader..

BUT have you considered running the SPSS in VMWare? I mean to install windows to a virtual disk (=file inside your home partition.) and running in a window or fullscreen under ubuntu? That is what I do. All windows programs that dont need fast graphics work fine in VMWare. (because it actually is a real windows installation.. just running under virtual machine.)

---

### Post by anaconda on 2007-01-11
> B) How can I take 5-10 gb off of the /home partition to install windows without messing up the grub?

well.. you will be messing with grub, and also your partition numbering might change so that you will have to edit your /etc/fstab accordingly.

---

### Post by Sarisar on 2007-01-11
You may find (as I did) that your legal copy of XP that came with your computer doesn't work under VMWare (but installs fine as dual boot).  Mine complains about the license key (which I double checked many times from the label stuck on my PC).  It's another annoyance with XP that it won't let you run your legal version on VMWare (and I thought it was under Vista they said you can't do the virtualisation unless you buy the full blown package and not XP)

But basically, my rule of thumb is install XP first as it tends to screw up boot loaders.  I did hear from someone else though that apparently 'it works fine now' but I wouldn't trust that for important data just in case...

---

### Post by gejr on 2007-01-13
Thanks for your answers. I've never considered vmware to be a viable option, but in this case I actually think it'll do the trick. Thanks for pointing me in this direction.

---

