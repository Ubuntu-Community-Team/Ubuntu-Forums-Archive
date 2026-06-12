---
title: "Hanging before GRUB..."
date: 2013-02-15
forum: General Help
---

### Post by S Hartwell on 2013-02-15
Well, I knew trying to install Mac was only going to cause problems when my DVD was possibly burned incorrectly. I'm certainly kicking myself now...

All I want is to get my Ubuntu working again.

Sadly, I think I made a mistake.

See, I have 2 HDD's and I'm pretty damn sure that I installed this Ubuntu on the bigger one(Sense the smaller one was mounted as a HDD not the filesystem.)

During the installation I had previously had a Ubuntu install on the smaller HDD(One I erased to place Mac on.) I'm wondering if somehow the two systems were connected...

All I do know I need is some help on what to do. All I get when booting to the smaller HDD is "B0 Error" which I've heard is a mac error. I really couldn't care less - No mac for me.

All I get from my old Ubuntu HDD is a blank screen with that blinking crusor. I'm guessing GRUB is simply messed up.

I'm downloading a new liveCD version now and I'll be making a bootable USB soon.

---

### Post by S Hartwell on 2013-02-15
Is there no-one out there that can help me?

I'll never be touching mac again and I'm going to make sure this never happens again. I just need to reinstall GRUB.

I figure my bootloader was on the smaller HDD w/o be noticing so.

PS: id use repair package thing you can dl but this desktop doesnt have internet w/o running some commands on my existing filesystem...

---

### Post by S Hartwell on 2013-02-15
Here's my report from Boot-Repair. Even that couldn't work. I'm ****** aren't I...

[http://paste.ubuntu.com/1659647/](http://paste.ubuntu.com/1659647/)

---

### Post by oldfred on 2013-02-15
Is this a Mac, we cannot help on Hackintoshs. See Forum code of conduct.

> Reinstall the GRUB of sdb1 into the MBR of sdb chroot: failed to run command `grub-install': Exec format error grub-install /dev/sdb: exit code of grub-install /dev/sdb:126


Do you have BIOS locked or virus protected?

---

### Post by S Hartwell on 2013-02-15
Where would I check if my BIOS is locked? It's been years since I've needed to alter BIOS(Aside from disabling my floppy drive today.)

If by 'locked' you mean via passwords, no. It is not.

---

### Post by S Hartwell on 2013-02-15
No, it is not a mac but I'm not asking for support for mac. I'm simply trying to restore my Ubuntu as I'm using a wireless adapter that would require some vicious coding to get running again...

---

### Post by oldfred on 2013-02-15
Some BIOS have virus software built in or Bit-locker which prevents writing to MBR. You have to go into BIOS and review all settings.

Otherwise you you may have to chroot into your install and see if it will install. But that is what Boot-Repair tried to do automatically.

---

