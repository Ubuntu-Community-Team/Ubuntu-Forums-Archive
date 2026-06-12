---
title: "file auto rename -&gt; FSCK0000.REN"
date: 2006-10-11
forum: General Help
---

### Post by FAT_C on 2006-10-11
hi everyone, i am newbe in linux and ubuntu, having trouble with the following situation~

i am using two OS together, which are windowsXPproSP2 and ubuntu 6.06. 
my windows is in english and so does the ubuntu
and i have many mp3's that are named in traditional chinese, since i am chinese.

the problem is, when i login into ubuntu, some of these mp3 file(or folder) rename by itself to FSCK0000.REN, FSCK0001.REN, FSCK0002.REN etc... and when i go back to windows, it wont change back to the original name. i dont want the name of the mp3 change to FSCK0000.REN or somethings else >_<

i noticed that the file's name will rename when only some of the chinese characters are existed on the name, such as "&#35377;", "&#36629;","&#21151;" etc..., 
for example, when the file name is called "&#35377;&#39000;&#27744;&#30340;&#24076;&#33240;&#23569;&#22899;.mp3" in windows, where the character"&#35377;" is in the name, it will be changed to "FSCK0000.REN" when i login ubuntu. 
and even if i change the name back in windows, once i login ubuntu, they rename it again.... 

my hard disk for the mp3 is in FAT32, and 
when i login ubuntu, i dont have to mount the hard disk, they just appear on the desktop.

does anyone know what the problem is and how can i fix it?
thx for help

---

### Post by FAT_C on 2006-10-12
why no one helps me??
anyone knows the solution???

---

### Post by PriceChild on 2006-10-12
It seems like a problem with dosfstools... [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg162119.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg162119.html)

If i were you i would file a bug on it at [http://bugs.ubuntu.com](http://bugs.ubuntu.com)

---

