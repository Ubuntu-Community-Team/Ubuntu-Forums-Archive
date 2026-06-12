---
title: "mount and see NTFS disk with 'root'"
date: 2005-04-22
forum: General Help
---

### Post by thewiper on 2005-04-22
Hi to everyone. I installed Ubuntu 5.04 and I start reading documentation. I am a linux newbie, coming from Yoper and Mepis. My problem, with Ubuntu, is this: I can't see my ntfs partition both with KDE and Gnome. These are the step I did:

1) Installing kde ;)
2) Log as the first choosen account
3) Modify the fstab as root (konsole->'sudo su kwrite')
4) From the konsole I type 'sudo su' to get root privileges then 'mount /dev/hda2/'
5) From the konsole (root) i can see my files in '/mnt/d' but not from kde. When I go to 'mnt/d' with Konqueror i see that folder locked by root and I can't browse it.

So i do this:

1) From Konsole 'sudo su konqueror'
2) With konqueror 'rooted' i change both permission and owner but a message informs me that i haven't enough privileges.

So? I'm missing something?
 ;-)

---

### Post by lorap on 2005-04-22
hi friend!
let's work it out.
first of all you'd know you can't edit files in ntfs partition from any linux.only fat32.
now let's get it connected:
1.create directory,say nt:
sudo mkdir /home/username/nt
2.connect to ntfs:
sudo mount /dev/hda0 /home/username/nt -t ntfs -o umask=000
3.to disconnect do this:
sudo umount /dev/hda0

p.s.:
it could be that your ntfs disk is hda1 or hda2,try to change numbers if it gives you an error the hda0 is busy.
have a nice day!
pavel

---

### Post by thewiper on 2005-04-22
[QUOTE=lorap]
first of all you'd know you can't edit files in ntfs partition from any linux.only fat32.
[/QUOTE]
Now i know! :) i suppose that newer version of kernel can do this. Ok, no problem 4 this

The method you suggested me works! Thank you a lot,  \\:D/

---

### Post by alex30002 on 2005-09-19
thx a lot  :)  \\:D/ 

ubuntu rulz

---

