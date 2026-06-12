---
title: "Problems with Shred"
date: 2007-11-06
forum: General Help
---

### Post by Catsworth on 2007-11-06
Hi Guys,

I have a USB stick mounted as /media/usbdisk which I would like to 'shred'.

I've tried:

```

shred --verbose /media/usbdisk

```

Which complains that it 'failed to open for writing: Is a directory'.

I've also tried:

```

find .-type f -execdir shred -u'{}'\;

```

Which complains that there is a 'missing argument to -execdir'


Anybody able to give me any pointers on what I'm doing wring here?  I basically want to shread every file on the drive, I will them rm -rf to remove the folders.

Thanks.

---

### Post by nixclusive on 2007-11-06
try shredding the whole raw disk there.. unmount the usb disk and shred the device file (/dev/???) instead. After that you can easily recreate the filesystem. Do you want more help with that?

---

### Post by Catsworth on 2007-11-06
Ok, I'll give that a shot - thx :)

---

