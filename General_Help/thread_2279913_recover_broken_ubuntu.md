---
title: "recover broken ubuntu"
date: 2015-05-26
forum: General Help
---

### Post by buill on 2015-05-26
hi i installed an update for ubutu on my latitude e6410 today and it killed the build it will not boot anymore i am trying to recover my documents from a debian live cd i had lying around but i never recorded my passphrase on the ubuntu build i have the hdd mounted but all the files are encrypted jibberish. do i have any options to recover the files or to undo the update???
thanks

---

### Post by RobGoss on 2015-05-26
If you don't mind me asking what was the update you took?

---

### Post by ajgreeny on 2015-05-26
So you are using encryption but can't remember the passphrase?

If that is what you are saying there is nothing you can do to recover anything as far as I'm aware; that is, of course, the whole reason for using encryption.
However, if you could boot to the system in the past, before the update, how did you manage that without the passphrase?

---

### Post by Vladlenin5000 on 2015-05-26
If I remember correctly - I did it once a long time ago, I usually don't use encryption in my own systems - there's a password and a passphrase; 

The password is what we need at boot time to unlock the drive;
The passphrase is a random (?) generated long string which is needed to access files in situations like this. Also I remember a warning about saving it somewhere and keep it safe, obviously.

OK, assuming you can unlock the drive then you might have a chance with Grub by booting an older kernel.
Otherwise there's no way and yes, that's exactly what encryption is for.

---

### Post by RobGoss on 2015-05-26
I my self never use [COLOR=#000000]encryption for this simple reason I feel my pass word should be good enough as long as you make it hard for others to access.[/COLOR]

---

### Post by buill on 2015-05-27
> **Vladlenin5000 said:**
> If I remember correctly - I did it once a long time ago, I usually don't use encryption in my own systems - there's a password and a passphrase; 

The password is what we need at boot time to unlock the drive;
The passphrase is a random (?) generated long string which is needed to access files in situations like this. Also I remember a warning about saving it somewhere and keep it safe, obviously.

OK, assuming you can unlock the drive then you might have a chance with Grub by booting an older kernel.
Otherwise there's no way and yes, that's exactly what encryption is for.

how do i booth with older kernal?

---

### Post by buill on 2015-05-27
k got it thanks that was easy :)

---

### Post by slickymaster on 2015-05-27
> **buill said:**
> how do i booth with older kernal?
During boot press and hold the left Shift key. This will bring up the Grub2 menu from where you can select "**Advanced options for Ubuntu**". After that you will be able to select the kernel you wish to boot in.

---

