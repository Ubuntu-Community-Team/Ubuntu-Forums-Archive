---
title: "Ubuntu Won't Load - I think it's my hard drive?"
date: 2008-05-28
forum: General Help
---

### Post by joshdudeha on 2008-05-28
Hello, today I just turned on my computer, and my internet wasn't working. So I rebooted, and it gets stuck at like 0.8 % and the hard drive it is saved on (there are 2 hard drives on my computer) just kept clicking. It has done it about 10 times now. Lately I have been having trouble with this hard drive. For example, the fan that makes it run - hasn't turned on very often.

And when I press Ctrl + Alt + F2 on the boot screen, it says something like
"Can't resume boot image" or something like that. And does so continually. 
I'm using Mandriva Live CD to post this - as my internet (being a usb adsl modem) won't work in hardy live. 
I'm not too worried about re-installing the whole system,
**But**, there is a folder that really needs putting onto a usb stick. The thing is, it can't be accessed from anything else than the ubuntu installation. =/ It won't even let me copy it. 
Could anyone help me with that?

Oh yeah, I would also like to note, that update-manager installed a new kernel today. But I don't think it made any difference, because both kernels do the same thing.

I am running Ubuntu 8.04 Hardy Heron.

Thanks for the help
---------------
Josh

---

### Post by MythosLegend on 2008-05-28
Have you tried the ubuntu live cd and mounting the partition/hard drive?

like

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu

where sda1 is the partition and hard drive
you can go into the ubuntu's partition root by

chroot /mnt/ubuntu /bin/bash

---

### Post by joshdudeha on 2008-05-28
Oh, I'll try that. Thanks.
Yeah, in the Hardy cd, it came with the same error, saying i didn't even have read access to the folder.
Just got to tell my dad how we need a new hard drive =/
I believe it is the hard drive.

---

### Post by MythosLegend on 2008-05-28
You can change ownership of the files to root.

chown newowner filename

where newowner is the user
You can also change the read/write properties with chmod. 
You might have to be in root or use sudo with those commands.

Good luck.

---

### Post by joshdudeha on 2008-05-28
Can you help me do that please?
I've mounted the drive into /mnt/hda1
but when i do chroot it comes up with "chroot: cannot run command `/bin/bash': No such file or directory
"

Could you help me with the above please, as I'm not too CLI-friendly

---

### Post by MythosLegend on 2008-05-28
I don't know what is causing that error. Perhaps you can try to go to the folders you want and change the read/write permissions.

---

