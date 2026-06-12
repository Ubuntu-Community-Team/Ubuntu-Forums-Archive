---
title: "Need help with clonezilla"
date: 2007-11-03
forum: General Help
---

### Post by bumanie on 2007-11-03
Before describing what I want to do, I would like to ask that no-one just post a link to clonezilla or a clonezilla tutorial. I have already looked at a number of 'help' sites and am still no clearer on how to use it. I have also searched the ubuntu forums for help, to no avail. Either I have a bad copy (md5checksum checks out OK), or I am doing something wrong.
I need to copy windoze to a slave drive so that I can reinstall windoze and get my mbr back. I have tried recovery console to fixmbr, but that did nothing. At present I have a dual boot system. So after I have fixed (hopefully) windoze, I want to clone feisty to the slave drive. I originally planned to install gutsy to the slave and that's when everything went wrong. Nothing in feisty would work and now the mbr and grub loader are wrecked. I have tried fixing both of them via methods suggested in these forums, but nothing has worked. I am able to boot the computer via super grub disk, but any settings /changes,  do not save. Once in, both OS's work fine, that is why I believe it is an mbr/grub problem only. 
Anyone a clonezilla expert who can give me a step by step tutorial? When I get up to the part that asks, where I want to send the cloned image to, I choose hdb1 and at that point clonezilla crashes - it does not respond to any keyboard inputs. Sorry that this is a bit long, but I don't want to have reinstall everything from scratch when the OS's seem to be operating perfectly.

---

### Post by pedja_portugalac on 2007-12-12
My problem is that the clonezilla 1.0.7-18, latest version, is unable to mount external HD of 500 GB. It is formated as fat32 and that way it is usable with allmost all operating systems. Thay say, it should be formated as ext3 for the best results but even like that it was unable to mount. When I was running dual boot, XP and Ubuntu, it was easy to make images with Acronis but now I am running just Ubuntu and that's why I need an alternative, Acronis doesn't make images of HDD with just Linux partitions. I found tutorial about clonezilla in the latest german PC Welt Linux edition and I was so happy but it seams it doesn't recognise large external drives? It's strange cause I have the latest clonezilla live cd with the latest kernel, it was realised on 10th December 2007. Does anybody knows some issue for this problem? :(

---

