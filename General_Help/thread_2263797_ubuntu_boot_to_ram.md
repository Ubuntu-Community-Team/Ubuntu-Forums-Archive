---
title: "ubuntu boot to ram"
date: 2015-02-03
forum: General Help
---

### Post by jimmyh1972 on 2015-02-03
Hi
I customized a 14.04 Ubuntu version using Remastersys and installed it on a USB flash device.
Is there a way to boot the whole system / session to ram eject the USB flash device and continue working?
Thank's ahead Jimmi

---

### Post by Mike_Walsh on 2015-02-03
Hi, Jimmy.

That sounds like quite an undertaking! I can't say as I've come across anybody trying this with Ubuntu before, although I won't say it can't be done. However; the way you've described that you want the system to work is EXACTLY how Puppy Linux works.....which I use myself.

Puppy was originally designed back in the days of very much older hardware, and was developed to work from CD, flash drive, floppy disks.....and even the old 'zip' drives. The whole thing averages between 150-200 MB, and is in the form of three files; vmlinuz, initrd.gz, and an .sfs file that contains the operating system itself. It decompresses into RAM at start-up, and then runs from there. The way it's arranged, you can then remove whatever medium you've booted it from, and use that drive for other things. You do, however, have to replace the medium when you shut-down, because it also contains a 'save-file' (created at first shut-down), where you save all the changes you've made during the session.

To be fair, that's not strictly true; you CAN put your 'save-file' onto any drive you wish.....as long as that drive is available to the system when you boot. You can have your O/S on the flash-drive, and your save-file on the internal HD (or an external one...or another flash drive...or a CD/DVD...or a 'floppy' even, should you still have one); the permutations are endless. Obviously, it's simpler to have them all on the same flash drive, as it then makes the system TRULY portable.

If you have a look on the Puppy forums, and explain what you're attempting to do, I'm quite sure some of the 'regulars' would be only too happy to give you further assistance. They're a good bunch.

[http://www.murga-linux.com/puppy/index.php](http://www.murga-linux.com/puppy/index.php)

Hope that helps!


Regards,

Mike. :)

---

