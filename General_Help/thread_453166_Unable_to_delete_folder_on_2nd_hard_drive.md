---
title: "Unable to delete folder on 2nd hard drive"
date: 2007-05-24
forum: General Help
---

### Post by alfreddo on 2007-05-24
Hi,

I am running Dapper Drake on an ex-Windows PC, which has a 2nd hard drive formatted by Fat32, so I can access this drive and both read and write to the old Windows files on it. But there  is a folder called 'Program Files' which contains backups of old Windows programs which I'd like to delete. The icon had a padlock on it, and when I try to move the folder to the wastebasket I get this message:

'Cannot move .... to the wastebasket because you do not have permissions to change it or its parent folder'.

When the PC was using the Windows OS this folder was not protected in any way, and the other folders on the 2nd hard drive are still not protected.

Any thoughts?

Thanks,

Alfreddo

---

### Post by renzokuken on 2007-05-24
easy way is to use the terminal since you have to be root to remove it (the padlock indicates you do not have any permissions on this file)

so say the folder is at /media/oldwin/Program\ Files/

you would run

```
sudo rm -r /media/oldwin/Program\ Files
```

which removes the folder and all its contents 
the "slash" between program and files simply lets the terminal know its is one directory with a space in the name

---

### Post by alfreddo on 2007-05-24
Thanks Renzokuken,

that worked OK as you said it would. Files now deleted.

Alfreddo

---

