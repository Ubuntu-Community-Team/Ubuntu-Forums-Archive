---
title: "How to open an ISO file with MC?"
date: 2007-03-13
forum: General Help
---

### Post by fantan on 2007-03-13
Hi,

Some times ago when I used the Dapper Drake distro, on those system I was able to open an ISO file in Midnight Commander very easy by clicking on it.
But in Edgy Eft I can't open ISO files in Midnight Commander.
When I click on the ISO file, I get the following error message from MC:
"ERROR"
"Non-consistent Extfs archiv!"

What this is mean?
How can I open ISO files in MC on my Edgy system?

Thank you for advance!

fantan

---

### Post by taurus on 2007-03-13
Applications -> Accessories -> Terminal
```
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop filename.iso /media/iso
```

---

### Post by fantan on 2007-03-14
Hi, 

Thank you very much for the answer, but I have a script like your commands and I can mount and/or umount several ISO files from ter4minal.
My problem is while in Dapper I was able to open an ISO file in Midnight Commander by clicking on it, but in Edgy this couldn't happen. 

Thanks anywhere.

fantan

---

