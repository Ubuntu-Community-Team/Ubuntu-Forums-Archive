---
title: "Can I hot swap a hard drive from one computer to another?"
date: 2020-05-19
forum: General Help
---

### Post by goemonburo on 2020-05-19
I have an old Dell Inspiron 530 circa 2007 and a newer but still ancient Dell Studio XPS 8100.  Both are running the same Lubuntu:  18.04LTS.  The drive in my newer XPS isn't bootable, and I used that to justify investing in a NEW system, a Dell XPS 8930.

I would like to know if I can simply hot-swap the older Inspiron drive (500GB) into the newer Studio XPS 8100 and expect it to work.  Could it really be that easy?!

I'm guessing no.  I believe the form factor is identical and that both are SCSI drives.  But do I need to worry about sectors and cylinders and BIOS stuff?  

Additionally, while sort of a different issue, I'd like to take the old drive out of the Studio XPS and have it as a second drive in the NEW system.  Will Grub be able to handle booting to that?  Especially if Grub DIDN'T handle booting to it before?  (I plan to put GRUB on the new system's main hard drive and have the old drive as a second disk.)

Any thoughts, help, suggestions would be great.  Thank you in advance.  (And if these two questions are really best asked/answered separately I can repost.)

(And maybe "hot swap" isn't the right term!!!  Maybe just swap?  I wouldn't be doing it while the systems are running!)

---

### Post by guiverc on 2020-05-19
I would have expected SATA (serial ATA) drives in a Dell Inspiron 530 which reminds me of consumer range more than high-end server drives which came with SCSI or SAS (serial attached scsi) drives.

I can't advice on booting a drive unchanged in another system. On an old [dell] box I wanted to upgrade *due swollen caps*, I ejected my real HDD & inserted an unused drive in the box, installed system, then did a test move to the newer box. This worked as I hoped, so I tried it on my wanted production drive being hopeful it'd work there too, nope. I may have been unlucky b/c of bad data on drive (reason I wanted to replace box), but I just opted to re-install in my new box anyway instead of look at why. Using it as a second drive, no issue; but personally I'd re-install a clean OS for the new system. In my example case; the old partition is used as /home. Booting to it works too, but in my case it'll boot and I can use the terminal, but I've done nothing to fix it's GUI (*it's now an older release than the newer release anyway being due for upgrade before move*).

If you're sticking with Lubuntu, you could use it to install Lubuntu 20.04 LTS.  Lubuntu 18.04 LTS was the last Lubuntu to use the LXDE desktop, all later releases use LXQt which requires re-install anyway.  From the [release notes]("https://lubuntu.me/focal-released/")

> ***Note***[COLOR=#555555][FONT=Ubuntu], due to the extensive changes required for the shift in desktop environments, the Lubuntu team does not support upgrading from 18.04 or below to any greater release. [/FONT][/COLOR]**Doing so will result in a broken system.**[COLOR=#555555][FONT=Ubuntu] If you are on 18.04 or below and would like to upgrade, please do a fresh install.[/FONT][/COLOR]

---

### Post by ActionParsnip on 2020-05-20
You can install the OS in one system then transfer it to another system. It will boot as you expect. Is this what you mean?

---

