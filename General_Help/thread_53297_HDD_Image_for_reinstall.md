---
title: "HDD Image for reinstall"
date: 2005-07-31
forum: General Help
---

### Post by Matchless on 2005-07-31
Hi,
        Does anyone know of a simple and foolproof way of making a backup image of the whole ubuntu installation,to restore/install again on same disk or another machine. Obviously the CD or DVD should be bootable. I have seen many discussions on this, but most of the procedures require a lot of caefull steps and a lot of 'if...then"  Is there an easy application available?
Regards
Matchless

---

### Post by flaming_monkey on 2005-07-31
It sounds like you want to clone (aka. ghost) your OS install to another system.  This is fine if the other system has the same hardware configuration, if it doesn't then you'll run into problems e.g running 32bit apps on a 64bit CPU.

I'm not to hot on the subject but there's some great information found [here](http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html) and a great tool [here](http://freshmeat.net/projects/g4l).

---

### Post by jeremy on 2005-07-31
partimage is what you need, like that overpriced 'ghost' product, but free, and works just as well!
I run it from a knoppix cd as it is not on the ubuntu live cd.

---

### Post by Franko30 on 2005-07-31
Hi,

thanks for the links - I've been looking around a bit for stuff like that myself.

For me (and maybe others) it is important to get an exact disk image, as the laptop I'm running Ubuntu on needed quite a few tweaks and saving the complete system would make sense, as  laptop hardware rarely changes. ;-)

Cheers

Franko30

---

### Post by Matchless on 2005-07-31
Thanks for the info. Yes, I want to reinstall on another similar machine, but I want to reinstall from a bootable CD if possible. The idea is to also use this to fall back to a "clean" install after playing around with some configs and installs or if crashing.
I have Knoppix, but have no idea how to use Partimage. If anyone has any guide on how to back up the complete HDD and restore to a HDD via CD or DVD I will appreciate.
Regards
Matchless

---

