---
title: "Problems with downloading with Firefox to network drive"
date: 2005-07-09
forum: General Help
---

### Post by MetalMusicAddict on 2005-07-09
I have a old 20 gig drive on my server I use to store downloads. In windows I download to if fine but in linux and using Firefox when the download finishes the file (say its a .tar) is corrupt. Happens every time. Weird?

---

### Post by MetalMusicAddict on 2005-07-11
Anyone seen an issue like this?

---

### Post by MetalMusicAddict on 2005-07-15
Last try. :)

---

### Post by arnieboy on 2005-07-15
[QUOTE=MetalMusicAddict]Last try. :)[/QUOTE]
have u tried copying the downloaded file onto ur local hard drive and tried unzipping it? does it still say its corrupt? sometimes when we try untarring directly from a remote server such error messages come up.

---

### Post by MetalMusicAddict on 2005-07-15
[QUOTE=arnieboy]have u tried copying the downloaded file onto ur local hard drive and tried unzipping it? does it still say its corrupt? sometimes when we try untarring directly from a remote server such error messages come up.[/QUOTE]
Thats interesting. :) Kinda defeats the purpose of a network download folder though. :)

Thanx man.

---

### Post by arnieboy on 2005-07-15
[QUOTE=MetalMusicAddict]Thats interesting. :) Kinda defeats the purpose of a network download folder though. :)

Thanx man.[/QUOTE]
no it doesnt defeat any purpose. check for permissions on the network folder. I am sure it does not allow users to execute files on the folder itself. this is done for added security. if u have set the permissions urself, u shd allow urself to have "execute" permission on files in that folder. then u shd be able to untar files directly from the folder on to ur local drive. does the shared folder belong to a windows server?

---

### Post by MetalMusicAddict on 2005-07-15
[QUOTE=arnieboy]no it doesnt defeat any purpose. check for permissions on the network folder. I am sure it does not allow users to execute files on the folder itself. this is done for added security. if u have set the permissions urself, u shd allow urself to have "execute" permission on files in that folder. then u shd be able to untar files directly from the folder on to ur local drive. does the shared folder belong to a windows server?[/QUOTE]

Here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               reiserfs notail          0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda4       /media/Storage  vfat    umask=000       0       0
//192.168.1.103/MP3s     /media/MP3s  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.103/Back-Up     /media/Back-Up  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.103/Bittorrent\040Server     /media/Bittorrent  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.103/More\040Movies     /media/MoreMovies  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.103/Video     /media/Video  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
//192.168.1.103/Camera\040Pics     /media/Fuji  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0
**//192.168.1.103/Downloads     /media/Downloads  smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0       0**
```

Theres the permissions for the folder. The owner for the folder is root. but when I look at the permissions tab for the folder all the r, w and ex boxes are checked for everyone. Im missing something I think. The fstab was done with help from the unofficial guide.

---

### Post by arnieboy on 2005-07-15
[QUOTE=MetalMusicAddict]Theres the permissions for the folder. The owner for the folder is root. but when I look at the permissions tab for the folder all the r, w and ex boxes are checked for everyone. Im missing something I think. The fstab was done with help from the unofficial guide.[/QUOTE]
I would look into the shared folder permissions from the windows machine... though ur unix permissions allow everything, ur windows permissions might override that.. check whether u have "execute" permissions in that folder from the windows machine.

---

