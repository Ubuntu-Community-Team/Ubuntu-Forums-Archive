---
title: "Lubuntu Read Only Options"
date: 2013-10-18
forum: General Help
---

### Post by isthatme on 2013-10-18
I have been trying to get a default install of Lubuntu to be able to boot read only. I know of no other way than editing the fstab to auto-mount as read only. I have added ro to the list of options for mounting the partition, however, when I do that it boots to cli only, and LXDE does not start, BUT it mounts fine as read only. (I had tested previously, with the stock options, and even with the file modified twice - once to try ro and once to change it back - and it worked fine). I cannot have the users run a script or anything to start LXDE as these are meant to be used in a school.

    I'm not sure as to the options I would ad to /etc/fstab, partly because the only default option listed is "errors=remount-ro", and partly because if I do add ro to the list of options it boots, just without LXDE.

Thanks, any help would be much appreciated.

---

### Post by danielr2 on 2013-10-19
Just a thought, have you considered BastilleLinux like this: [http://users.telenet.be/mydotcom/howto/linuxkiosk/kioskbastille.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/kioskbastille.htm)

---

### Post by steeldriver on 2013-10-19
It does sound like a kiosk-type system is what you should be looking at

I'm not an expert in this kind of thing but I would think you need at least a rw /home partition in order to start an X session (the X server needs to create an .Xauthority file in the user's $HOME)

---

