---
title: "md5 checksum mischief"
date: 2007-08-07
forum: General Help
---

### Post by Hemonator on 2007-08-07
Anyone who can explain this? I'd like to try out suse just for the experience, but... It's kinda hard to get a decent iso with right md5... Ive DLled the DVD 3 times and the CD1 4 times. Always the same thing. See for yourself.

janne@janne-desktop:~$ md5sum --binary openSUSE-10.2-GM-i386-CD1.iso
2f120c676eb63a8c6473b7b0fd14bf96 *openSUSE-10.2-GM-i386-CD1.iso
janne@janne-desktop:~$ md5sum --binary openSUSE-10.2-GM-i386-CD1.iso
c1c4dfeac162c52820273c6dcdd6aec9 *openSUSE-10.2-GM-i386-CD1.iso
janne@janne-desktop:~$ md5sum --binary openSUSE-10.2-GM-i386-CD1.iso
fb95cd3ab6f01fce17ccdc571bf4e5af *openSUSE-10.2-GM-i386-CD1.iso
janne@janne-desktop:~$ md5sum --text openSUSE-10.2-GM-i386-CD1.iso
cc28e3d4c92a1394c2c0375a036b4546  openSUSE-10.2-GM-i386-CD1.iso
janne@janne-desktop:~$ md5sum --text openSUSE-10.2-GM-i386-CD1.iso
82f02a873983aec038b022db36d1bd94  openSUSE-10.2-GM-i386-CD1.iso
janne@janne-desktop:~$ md5sum --text openSUSE-10.2-GM-i386-CD1.iso
9c33367c7571ed635cbb1a6d0e0b2ad6  openSUSE-10.2-GM-i386-CD1.iso
janne@janne-desktop:~$ md5sum openSUSE-10.2-GM-i386-CD1.iso
ca865fa21c58e3f5d7fa2643063acdb4  openSUSE-10.2-GM-i386-CD1.iso
janne@janne-desktop:~$ md5sum openSUSE-10.2-GM-i386-CD1.iso
9030ec37ce9f83da0cc89c8f0f813fbd  openSUSE-10.2-GM-i386-CD1.iso

I DLled the file with wget from opensuse site. It's not under any process nor getting fixed by some torrentware. I ran killall wget just in case, but there was none open. I'm using Ubuntu Feisty fresh installation.

---

### Post by dfreer on 2007-08-07
Wow... try rebooting, then running your md5sum. I can't think of any reason why you would be getting different values unless the file is being modified somehow.
You could also try making it a readonly file, and see if you get the different values.

---

