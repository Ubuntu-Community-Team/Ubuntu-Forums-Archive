---
title: "rsync is not smart using samba"
date: 2007-02-21
forum: General Help
---

### Post by jmvidalvia on 2007-02-21
I use:
**rsync -avz /media/hda5/Fotos/ /media/usb/Fotos/**
and everything goes find. Only new files are copied to an external usb drive.

Then I plug this usb drive to my network using NAS, and mount a samba volume in my linux.
**smbmount //my.nas.local.ip/drive1 /mnt/nas -o ,uid=myname,gid=mygroup**

Everything seems ok, I see my data.
But when I do:
[B]rsync -avz /media/hda5/Fotos/ /mnt/nas/Fotos/
[/B]
All files are copied once, and twice, etc.
Rsync just know how to copy, it overwrites for ever and ever same files.
¿any idea about what can be happening?
Thanks a lot!

---

