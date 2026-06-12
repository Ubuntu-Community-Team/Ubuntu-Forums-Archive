---
title: "Help! Accidentally ran mkfs.exfat on my ext4 home directory partition. Reversible?"
date: 2014-02-16
forum: General Help
---

### Post by NickMcRump on 2014-02-16
While attempting to update the file system of a flash drive, I accidentally supplied mkfs.exfat with my home directory's partition path instead of the flash drive's. Is there anyway to reverse this? Feeling a bit sick to my stomach as it's been a while since I've backed up my data, and this was such an amateur mistake.

---

### Post by dragonfly41 on 2014-02-16
I know little about exfat recovery .. but there is always a ray of hope using testdisk .. from a Live CD

[http://forum.cgsecurity.org/phpBB3/big-oops-can-testdisk-fix-this-t2815.html](http://forum.cgsecurity.org/phpBB3/big-oops-can-testdisk-fix-this-t2815.html)

but you will need to read up on using testdisk from the testdisk forum .. and I would consider taking the first step of cloning your corrupted partition so that you try to recover the clone not the original.

Live CD with clonezilla and a spare external drive for your clone would be the way I would go.

---

### Post by fdrake on 2014-02-16
Use photorec. You'll need a live cd (either ubuntu or  BootMed Live CD)
tutorials:
1:[http://www.bootmed.com/bootmed/tutorials-11/how-to-recover-deleted-files-with-photorec/](http://www.bootmed.com/bootmed/tutorials-11/how-to-recover-deleted-files-with-photorec/)
2.[http://www.linuxforu.com/2009/05/recover-deleted-files-easily-with-photorec/](http://www.linuxforu.com/2009/05/recover-deleted-files-easily-with-photorec/)

---

