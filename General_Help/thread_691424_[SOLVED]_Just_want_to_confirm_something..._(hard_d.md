---
title: "[SOLVED] Just want to confirm something... (hard drive related)"
date: 2008-02-08
forum: General Help
---

### Post by smacattack on 2008-02-08
Okay I want to do something I just want to confirm that it sounds right...

I have a primary hard drive with Windows on it and a secondary with Ubuntu on it.

The primary is nearing the end of its life (it keeps me up at night if i leave it on it makes such awful noises lol) and I want to disconnect it and make the secondary, with Ubuntu, my primary.

So as I understand it I just have to change the jumpers on the hard drives and make my secondary, which is currently a slave, into a primary. Should work, right? I don't mind if I have to reinstall Ubuntu or whatever so that won't be an issue. Is that all that I would have to do... like is it just in the BIOS that you pick it to boot or is changing the jumper enough?

---

### Post by Therion on 2008-02-08
My suggestion:

Pull the IDE cable and switch the Primary/Secondary connectors (assuming both drives are using the same channel).

Switch the Master/Slave Jumpers.

Boot, go straight to the BIOS and confirm both drives are being recognized correctly and that the boot sequence is correct (in relation to the drives specifically).

Since both drives have an OS on them, you should be good to go.

---

### Post by Rocket2DMn on 2008-02-08
It sounds like you want to get rid of the windows drive completely.  Have you tried just disconnecting it from the IDE cable and booting the computer?  You may not have to change anything else.  If it doesn't let you boot with the drive on slave, you can put it on the master IDE connector, set the jumpers, then boot the computer.  If GRUB gives you errors, you will have to reinstall GRUB - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)
You may have to check your fstab file, too, once you're back in Ubuntu.
```
gksudo gedit /etc/fstab
```

---

### Post by smacattack on 2008-02-09
mission accomplished. i switched the IDE cables and jumpers and it booted just fine and  all is well. im glad my windows drive has now arrived in hard drive heaven :)

thankyou both.

---

### Post by Rocket2DMn on 2008-02-09
> **smacattack said:**
> mission accomplished. i switched the IDE cables and jumpers and it booted just fine and  all is well. im glad my windows drive has now arrived in hard drive heaven :)

thankyou both.

Funny, I would've thought a drive with windows would go the *other* way!
:lolflag:

---

