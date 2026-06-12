---
title: "Philips Dvd+-rw Dvd8631"
date: 2005-08-27
forum: General Help
---

### Post by snowjunkie on 2005-08-27
Hi,

I couldn't get the Live CD to work with the Philips DVD8631.  It got to the boot screen and through stage 1 or so of the bootup (i.e. it seems to be reading files off the cd ok).  Then it claimed it could not detect a cdrom drive!

I could get it working ok on another dell computer (different spec) and a dell inspiron laptop.

Has anyone any ideas?

Alastair Vance.

---

### Post by timelf123 on 2005-08-31
Are you running a Dell 8400?

---

### Post by snowjunkie on 2005-08-31
Yes, I am... why?

---

### Post by timelf123 on 2005-08-31
If you are running Windows on the computer also, you are out of luck for the time being. The only way to fix this problem is to go into the BIOS and change the SATA operation settings (see [https://wiki.ubuntu.com/InstallingUbuntuOnaDell8400](https://wiki.ubuntu.com/InstallingUbuntuOnaDell8400) for instructions of you don't have another operating system). What that guide fails to tell you is that if you do switch the setting, Windows refuses to boot, and you are stuck with non-working drive (even the fixmbr and fix boot tools did nothing for me). I ended uphaving to reformat my Windows drive and I gave up on Ubuntu until I found this link [http://cdimage.ubuntu.com/releases/breezy/colony-3/?C=D;O=A](http://cdimage.ubuntu.com/releases/breezy/colony-3/?C=D;O=A)  . Breezy Badger installed great for me because it has a newer kernel the 5.04 did.

Good Luck!

Tim Elfelt

---

### Post by snowjunkie on 2005-09-01
Good job I didn't try to install it then!  Thanks for the warning.  I was only trying the LiveCD on my 8400.
I have ubuntu running quite happily on my dell inspiron 6000 with xp pro.

Thanks again,
Alastair.

---

