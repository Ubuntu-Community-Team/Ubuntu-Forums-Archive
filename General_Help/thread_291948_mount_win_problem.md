---
title: "mount win problem"
date: 2006-11-03
forum: General Help
---

### Post by binary_dream on 2006-11-03
Hi folks, 

I very new in Linux, actually I just installed ubuntu :D though installation went fine with my notebook - HP.

I need now to mount windows (I have to partitions one for winXP and one for ubuntu), but I wanna be able to see files on windows side, so I learned that I have to mount windows and I tried this:
> 
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222


but I get this error:
> 
Wrong fs type, bad option, bad superblock on /dev/hda1,
missing codepage or other error
....
..


What do I have to do in order to mount it? that way obviously is not working :(

Another question is how do I know if all the drivers were installed correctly in my notebook? I hear a lot of people talking about yast do we have yast in ubuntu ?


Thanx a lot, and pardon my ignorance

---

### Post by PriceChild on 2006-11-03
*thread moved*

---

