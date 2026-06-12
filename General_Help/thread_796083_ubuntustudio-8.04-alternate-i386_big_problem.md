---
title: "ubuntustudio-8.04-alternate-i386 big problem"
date: 2008-05-16
forum: General Help
---

### Post by fantan on 2008-05-16
Hi for all,

Some days ago I've downloaded the ubuntustudio-8.04-alternate-i386.iso and tried to install it on another partition on my computer. It has several partitions, on one of them I have Hardy Heron 8.04 LTS final yet, which is working very well.
I checked the downloaded ISO threee times: after downloading the md5sum; after burning on the DVD with k3b; and before installation.
The installation DVD is fully errorfree!
I've installed the ubuntustudio, did all upgrades, but when I want to change video driver to nvidia both with help of built "restricted device drivers" option or with help of envyng-gtk, after rebooting the computer, and by starting X, the computer totally freezes!
Luckily using the Hardy Heron 8.04 I can rewrite the xorg.conf of the ubuntustudio from nvidia to vesa so the X of ubuntustudio works with vesa driver, but the screen of monitor in this case is moving left approxiately 5 mm.
What is with this thing in ubuntustudio and how to fix it?

Can anybody help me?
Thanks for advance!
fantan

---

### Post by EXCiD3 on 2008-05-16
What video card are you using?

---

### Post by fantan on 2008-05-16
If I remember properly, my videocard is nVidia with 128 MB of videoRAM but I don't know the exact type.
I'm familiar with "restricted device drivers" option and envyng too.
Both of them do the recognition of the videocard automatically.
Anyway, on the same hardware the Hardy Heron 8.04 LTS configuration is working fine, without any probem. What's more Compiz Fusion here is working wery well too.

---

### Post by EXCiD3 on 2008-05-16
hmm thats interesting. i wouldnt think that ubuntu studio would be much different in configuration than regular hardy heron. Since ubuntu studio is basically a customized version of ubuntu, you can always just convert Hardy to Ubuntu studio seeing as your graphics card works fine in it already as they do in this thread: [http://ubuntuforums.org/showthread.php?t=794423](http://ubuntuforums.org/showthread.php?t=794423)

They mention installing the real time kernel, this could be what is causing the nvidia issue. You may try leaving everything but if you decide to convert ubuntu to ubuntu studio.

---

### Post by fantan on 2008-05-16
Thanks a lot for the idea!
I'll install the Hardy Heron 8.04 LTS on the partition where now resides the ubuntustudio and try whether the rt kernel causes the problem. 

Thanks again!

fantan

---

