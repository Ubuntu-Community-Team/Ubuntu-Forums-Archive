---
title: "No Safe Mode in Grub - how to I start in safex mode ?"
date: 2014-02-19
forum: General Help
---

### Post by OpenInformation on 2014-02-19
I updated my video driver to a newer one and the gui comes up black.


Lubuntu 12.04

Supposed to be a safex option in GRUB but it is not showing.

Boots to command line.

I can boot with the live cd and then what? edit etc/xorg.conf to add vesa driver?

---

### Post by slickymaster on 2014-02-19
To boot in "recovery mode", hold the left Shift key during the boot press. This will bring up the Grub2 menu from where you can select the _"Advanced options for Ubuntu"_. After that you will be able to select the kernel you wish to boot in _"Recovery mode"_, which will lead you to the advanced options.
By selecting _"Enable networking"_ you'll gain access to your network and the internet for upgrades or downloads, and will also mount your hard drives in read/write mode in case you need to edit files.
After the network has loaded, and file-systems are mounted, you will be presented again with the menu, from where you can choose _"Drop to a root shell propmpt"_.

Note that you are root in this shell. Hence no sudo is needed for administrative tasks. **This also means you will have full access to all files, and it may cause irreversible damage to your system if you make any mistakes**_._

If you do not enable read/write access with "Enable networking" the file-system will be mounted read only, and you'll be unable to edit files.

---

### Post by OpenInformation on 2014-02-20
Finally ended up re-installing Lubuntu (7 minutes )

Tried booting up with network enabled - got stuck
Tried Slitaz live cd - got stuck
Tried Lubuntu live CD - could not write to disk

Tried creating xorg.conf and copying it to the X11 folder in etc, no permission to do so.

Installed without formatting hard disk, wireless adapter not working, mouse intermittently not working, did a format and re-install

Anything I could have done differently?

---

