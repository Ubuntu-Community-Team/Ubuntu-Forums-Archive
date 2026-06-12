---
title: "linuxwacom from source in gutsy, what's the right way to do it?"
date: 2007-10-27
forum: General Help
---

### Post by oedipuss on 2007-10-27
I'd like to try the newest version of linuxwacom, due to some marginally annoying problems. Namely, a single click often registers as a double click. So I'd like to see if linuxwacom 0.7.8 or 0.7.9 are any different.

I know how to build and install the linuxwacom driver, but I'm not at all sure what to do with the already installed kernel module and xorg drivers from the ubuntu repos. 

So, would it be safe to just ignore the xserver-xorg-input-wacom package and kernel module and overwrite the files as necessary (risking of course that an update would again replace those files), or should I uninstall them, and if so, how ? Removing the xorg-input-wacom package also removes some metapackages that I'd like not to mess with, and I've no idea where the kernel module is, or if it's safe to remove it.

Thanks =)

---

### Post by suchawato on 2007-10-27
As far as replacing , I'm not sure, but I do believe that the double-click glitch is fixed in the latest version.
I use a serial tablet, and am still messing with that.
I would be interested to know the answer too, but I somehow think that installing the new version would be just fine.
did you check the wacomlinux website for questions regarding upgrades?

---

### Post by oedipuss on 2007-10-27
I couldn't find anything in the mailing lists and the howtos. It's mostly an ubuntu related question though. 

Hmm if you think its safe too,  I'll try just replacing everything; removing 'xserver-xorg-input-all' makes me rather nervous, even if it's only a metapackage lol

PS: it's so nice to see someone with the exact same problem.. I was starting to think there was something wrong with the device itself XD

---

### Post by suchawato on 2007-10-27
I would backup your xorg.confg file and then edit it.
not 100% sure its safe to just delete it all.

---

