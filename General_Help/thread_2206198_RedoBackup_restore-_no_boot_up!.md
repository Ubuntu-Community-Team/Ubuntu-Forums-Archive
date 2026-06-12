---
title: "RedoBackup restore- no boot up?!"
date: 2014-02-17
forum: General Help
---

### Post by PDA1 on 2014-02-17
RedoBackup made a backup of a 16g USB stick (which supposedly, or so I thought, contained the entire operating system and data files). I then restored the image to  another USB stick of the same size (16g). There were no error messages.

The new USB stick wouldn't boot up when I went to use it. There's was  just a black screen. I tried several times to reboot the usb stick to  no success.

Having said that. Then I reinstalled grub-[http://crunchbang.org/forums/viewtopic.php?id=15351](http://crunchbang.org/forums/viewtopic.php?id=15351) and all worked perfectly.

What went wrong? Why wasn't grub installed?

---

### Post by mastablasta on 2014-02-18
perhaps you didn't backup the whole disk but maybe sdb1 partition (if sdb1 is on USB)?

as i understand it is a bit-by-bit bare metal clone that is created and upon resotre if you backup up the whole disk grub should be restored as well.

---

