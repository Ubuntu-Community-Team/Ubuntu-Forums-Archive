---
title: "I extracted a Mint iso file onto my desktop, now I can't delete it."
date: 2014-11-11
forum: General Help
---

### Post by caleb16 on 2014-11-11
I've tried chmod 777 everything in that folder and file, but I still get
rm: cannot remove ‘boot’: Permission denied
rm: cannot remove ‘casper’: Permission denied
rm: cannot remove ‘dists’: Permission denied
rm: cannot remove ‘EFI’: Permission denied
rm: cannot remove ‘isolinux’: Permission denied
rm: cannot remove ‘pool’: Permission denied
rm: cannot remove ‘preseed’: Permission denied
rm: cannot remove ‘README.diskdefines’: Permission denied



What have I done :(

---

### Post by caleb16 on 2014-11-11
Nvm opened a terminal sudo -u root rm -R Mint
=D

---

### Post by jimmyh1972 on 2014-11-12
you cant remove objects like that without being a root
go sudo and then any other **rm** command or any other delete options :-)

---

