---
title: "GRUB and Windows MBR Issue"
date: 2008-01-27
forum: General Help
---

### Post by MrMarf on 2008-01-27
Hi All,

I just used the Ubuntu 7.04 CD to install ubuntu to my 4gb usb drive with the intention of making a mobile ubuntu install.

Stupidly I did not remove the hard drive from my laptop before starting the installation, and now GRUB has been installed on it, and the OS boot menu will not load without the USB drive connected, it tells me error 21.

If I start up with the USB Drive connected, I get the grub boot menu which shows the Ubuntu install on the USB Drive and my XP installation.

How can I undo this? I do not want a grub boot menu on my laptop. Its my work laptop :/

I have windows xp and as its my work laptop I do not have the administrator password.

Any help greatly appreciated

Thanks

Marf

---

### Post by danwood76 on 2008-01-27
if you insert the XP install disk and let it load up you will get to a menu which allows you to drop into a command prompt (recovery console or something) you can then run ```
fixmbr
``` to replace the MBR with the standard widnows one and everything will be back the way it was.

What you should have done on the install was tell grub to install on your pen drive and not the MBR.

regards,
Danny

---

### Post by MrMarf on 2008-01-27
Danny, I'd need the admin password to use the recovery console though, wouldnt I?

I don't have that password, its my work laptop.

Also when I installed Ubuntu it did not give me the option of choosing a location for Grub

---

### Post by MrMarf on 2008-01-27
bump

---

### Post by danwood76 on 2008-01-27
No you dont need the admin password to do the recovery console. Just an XP install disk.
You let it boot so far and it asks you if you want to install or recover, choose recover then run fixmbr and possibly fixboot aswell.

regards,
Danny

---

### Post by MrMarf on 2008-01-27
I'll give it a try,  thanks :)

---

### Post by MrMarf on 2008-01-29
fixed it with this

[http://www.download.com/MbrFix/3000-2094_4-10485990.html#](http://www.download.com/MbrFix/3000-2094_4-10485990.html#)

---

### Post by lswest on 2008-01-29
quick comment: XP Pro (probably what's installed on the laptop) needs an admin password.

---

### Post by danwood76 on 2008-01-29
Correction you dont.
I used to run XP pro and to access the recovery console, which doesnt even require logging in to your PC or booting windows, it just goes straight in.

Its just another option in the install.

Plus XP pro doesnt have an Admin pass by default.

---

### Post by lswest on 2008-01-30
well, usually companies do add an admin password to Pro installs during set up, i add a password to mine too, just to prevent people from messing around.  However, of course, if you don't set one up, it doesn't ask for it.  I just meant IT guys at a company are likely to have a password set up.

---

### Post by danwood76 on 2008-01-30
That still doesnt dispute the fact you dont require one for the recovery console :)
The only problem with setting a admin password in XP is that it can be deleted as easily as its set ;) still I dont want to bash microsoft security policies too hard. ;)
Sorry if I sounded a bit short in my other post, it was late.

kind regards,
Danny

---

### Post by lswest on 2008-01-31
not a problem at all, realized after i said it that it wasn't clear what i meant:P sorry about that^^

---

