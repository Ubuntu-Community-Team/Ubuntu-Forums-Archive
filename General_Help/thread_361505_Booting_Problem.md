---
title: "Booting Problem"
date: 2007-02-14
forum: General Help
---

### Post by ddollas on 2007-02-14
I'm not sure where to put this but I certainly need some help.  I just had a random power outage, and afterwards I'm getting the error message, "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)"  I'm using edgy Eft.  I'd like to find someway to keep my files if you could, I am not looking forward to cofiguring everything correctly again :/  Please Help.  Just in case it needs to be stated, my desktop won't boot and I am on my Laptop.

Also before the Kernal Panic error there is a crc error

---

### Post by mgmiller on 2007-02-14
It's possible you damaged some of your RAM when the power went out.  If you can, go into your BIOS and change the quick power on self test to the full test, so it scan your memory, see if that helps.  Also, if you have more than 1 stick of RAM, try only booting with 1 stick at a time to see if that makes a difference.  I think,somewhere in the Ubuntu bootup menus there is a memtest feature as well, try hitting the esc key to enter GRUB before the graphical part of boot starts and look for a memtest command.   When you get it all sorted out, get a good uninteruptible power supply that also controls brown outs, not just black outs.

---

