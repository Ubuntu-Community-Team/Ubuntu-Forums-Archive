---
title: "Unformat ext3 help (search didn't help)"
date: 2007-02-22
forum: General Help
---

### Post by someonestolecc on 2007-02-22
It was late at night and I ticked the wrong box when I re-installed Edgy. Consequently I formatted my user partition which I'd love to get back.

I haven't written ANY data to that partition. I also purchased another HDD so I can do recovery if necessary.

Through searching however, I've determined that most recovery programs recommended are just that - data recovery tools.

I'm after an unformat tool. Basically something that will look past the journaling/FAT (not sure what it's called in EXT FS) information, look at the actual data, and rebuild the journaling/FAT info.

I'm currently thinking, since I can't find unformat tools for ext3, that perhaps I can copy the raw with dd_rescue which will create an image file. I'm hoping that image file itself will contain the journaling information (surely that's what it rebuilds no?)

But it would be great to find something that has the ability to just rebuild my journaling by reversing the format command.

Anyone have any tips? Or has successfully reversed an ext3 format by the installer (i'm assuming it's quick format because it took about 3 seconds).

Thank you............................................ :|

---

### Post by gozzerd on 2007-02-22
wow. I'm not sure what's left after something like that. I don't understand the nature of the superblocks and such well enough to be sure. But I did recover everything after accidentally formatting my drive with MSDOS format command, which is supposed to be worse. The most invaluable tool was the program testdisk. it will scan and look for all the old remnants of partition tables, boot sectors, and such and try to give you the info you need to reconstuct things. It's available on Knoppix, UBCD (ultimate boot cd) and some other rescue tool type disks. Probably Puppy, too, which will run fast. took me hours and hours, but eventually I got it all back, more or less. It would be good to have an extra harddrive you can pop in as a new primary and work on the damaged disk as an unmounted secondary. Good luck

Geoff

---

