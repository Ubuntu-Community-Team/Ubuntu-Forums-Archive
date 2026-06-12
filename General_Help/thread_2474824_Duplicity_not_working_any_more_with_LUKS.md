---
title: "Duplicity not working any more with LUKS"
date: 2022-05-09
forum: General Help
---

### Post by ewanb2 on 2022-05-09
Hi,
I've been using Deja Dup with an LUKS encrypted external USB drive without problems until yesterday. 

Deja Dup now gives the error on backup: "Giving up after 5 attempts. Error: Error opening directory '/media/ewan/tiny backup': Permission denied"

I can see the disk in Disks and can lock and unlock it through the Disks UI which offers to fill in the passphrase telling me 'The encryption passphrase was retrieved from the keyring'

If I lock the disk and then navigate into it using Files there's a wait and then I can see the duplicity files.

Any idea how to get Duplicity working again ?

Cheers, Ewan
(this is on Ubuntu 20.04.4 LTS)

---

### Post by ewanb2 on 2022-05-09
Fixed...the mount directory had changed for some reason (a '1' appended to the end)

---

