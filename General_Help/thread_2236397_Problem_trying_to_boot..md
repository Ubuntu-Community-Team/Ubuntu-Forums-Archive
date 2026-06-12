---
title: "Problem trying to boot."
date: 2014-07-26
forum: General Help
---

### Post by Jerfo on 2014-07-26
Here is my problem, I tried booting my Ubuntu partition (14.04), while it does show up in GRUB afterwards it fails to boot, so I tried to run from a live-usb and using the disk analyzer I tried to load that same partition and I get an error message, something about "error mounting /dev/sda1 ... exited with non-zero status 32:mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program or other error"

Other odd thing was that I tried to boot from my Mint partition and it gave me an error about the X server being missing (haven't used it in quite a while but last time I had used there was no such problem), the disk analyzer could load that partition without errors. I'm thinking of using of the live-usb to repair my ubuntu installation but I don't know if there's something else I should do.

Add.: I ran a self test for the HDD and both the extended and short failed... I'm guessing this can't be good.

---

### Post by dragonfly41 on 2014-07-26
The clue in your error message I would focus on is .. "bad superblock"

search for tips/links/tutorials on that subject ... "recover bad superblock"

e.g.  [http://ubuntuforums.org/showthread.php?t=2234024&highlight=bad+superblock](http://ubuntuforums.org/showthread.php?t=2234024&highlight=bad+superblock)

---

### Post by sandyd on 2014-07-26
> **Jerfo said:**
> Here is my problem, I tried booting my Ubuntu partition (14.04), while it does show up in GRUB afterwards it fails to boot, so I tried to run from a live-usb and using the disk analyzer I tried to load that same partition and I get an error message, something about "error mounting /dev/sda1 ... exited with non-zero status 32:mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program or other error"

Other odd thing was that I tried to boot from my Mint partition and it gave me an error about the X server being missing (haven't used it in quite a while but last time I had used there was no such problem), the disk analyzer could load that partition without errors. I'm thinking of using of the live-usb to repair my ubuntu installation but I don't know if there's something else I should do.

Add.: I ran a self test for the HDD and both the extended and short failed... I'm guessing this can't be good.

The fact that you have extended and short test failures indicates possible disk failure/corruption, I would advise backing up your data after you've recovered it and use another hard disk.

---

