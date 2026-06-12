---
title: "224GB free = &quot;no space left on device&quot; ???"
date: 2007-06-09
forum: General Help
---

### Post by kazmatic on 2007-06-09
Hello all,

I am a relative novice, but do occasionally poke around in a terminal, mostly for managing large numbers of files. I recently switched from and old (OLD!) version of Debian to Ubuntu 6.06 from a CD someone had lying around. I was happy to find I could connect my USB drives (500GB Maxtors) and start utilizing space that was hitherto inaccessible through the old version of Debian. 

However, while attempting (in the GUI) to backup a very large (>300GB) directory on an existing internal HD, Ubuntu interrupted with an error stating there would not be enough space on the drive. I thought it might just be a GUI bug, so I tried cp -r ... and dusted my hands off. I came back a few hours later to find that it had gotten through about 230GB and started printing errors that all said something like "cannot copy .... no space left on device" 

Oddly, when I run df -h the computer happily admits there is at least 224GB left on the drive. I've tried searching forums for this, but I've had trouble locating anything. If this sort of question has been answered already, just point me in the right direction. Otherwise HELP!

Cheers,
Kaz

---

### Post by ikonia on 2007-06-09
tell is where you are copying from and to,

put the output of df -h on here too.

show us the exact command your using.

If possible show us the exact message.

Are you booting from the livecd - or from an actual linux install.

---

### Post by kazmatic on 2007-06-09
so the command I'm using is simply 

cp -ru /disk2_1/back-ups/feynman /media/external

Which creates the folder "/media/external/feynman" just fine. When I do df -h I get, along with the internal drives  and stuff, 

Filesystem          Size    Used  Avail     Use%    Mounted on
...
...
dev/sda1          466G  243G   224F    53%   /media/external
...
...

Does that help at all?

Thanks,
Kaz

---

### Post by kazmatic on 2007-06-09
Oh, and the error message says

cannot copy .... to ....: no space left on device

and I'm booting from a Linux install

Thanks,
Kaz

---

### Post by Lord Illidan on 2007-06-09
Can you delete all the files you copied and retry the df -h command?

BTW, make sure you delete the files by using SHIFT+DELETE. Just pressing DELETE will move the files to a .Trash directory on the external hdd, thus not freeing any space.

---

