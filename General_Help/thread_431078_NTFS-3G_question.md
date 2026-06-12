---
title: "NTFS-3G question"
date: 2007-05-02
forum: General Help
---

### Post by NIKOSHIBA on 2007-05-02
hey there,
read and write going well.
Problem: every folder i make on ntfs partition owned by root, although i can create and delete it. i tryed to ```
chown username:users /mountpoin
``` but it doesn't work!!! owner and group are still root. it is irritating because i'm trying to export my /home to much larger and shared ntfs partition, but because of this ownership issue i get error message during login. Although afterwords everything going well.
How do i change ownership and group? 
plz help

---

### Post by 50words on 2007-05-02
I have experienced a similar problem, and would love to know how to change the owner of a whole directory and everything underneath it.

---

### Post by kelvin spratt on 2007-05-02
i store in ntfs but do not use it as the home folder i have separate root ext3 home ext3 partitions swap ext2
the rest of my hardrives are ntfs i write direct to the ntfs partions all 5 of them with no restrictions
i think you need to separate your home partition and make it ext3 as there are restictions on permissions on the home folder

---

### Post by 50words on 2007-05-02
For me, ext3 is not an option. Windows Desktop Search will not index an ext3 partition, and Windows is still my primary OS.

You can set it to read and write the /home partition without too much trouble. But I could never figure out how to change the owner.

---

### Post by NIKOSHIBA on 2007-05-03
> **kelvin spratt said:**
> i store in ntfs but do not use it as the home folder i have separate root ext3 home ext3 partitions swap ext2
the rest of my hardrives are ntfs i write direct to the ntfs partions all 5 of them with no restrictions
i think you need to separate your home partition and make it ext3 as there are restictions on permissions on the home folder

i have considered this option, it would work best and without a hastle. But what kind of freek i would be not to try to do something that gives me an headake!!!
Actually i want to try utilise most HD space. i tripple boot: win, suse, ubuntu (then comes swap, and then my DATA ntfs partition). making separate partition only for home (shared), say 10-15GB for both linux installs, would mean loosing few GBs of disk space - since i will never store there anything. this is why i got one big ntfs partition for DATA storage, and there i want to have my /home too.
i'm sure i am exagurating with HD space and all, but i think this sort of mazochistik idias make me learn about linux even more.
so....if anyone got a solution, bring it...

ps. my spelling sucks i know (just hope you could make some sence of things i have written)

---

### Post by NIKOSHIBA on 2007-05-04
so.....no one has any idea?

---

### Post by patrickfromspain on 2007-05-04
you can't chown a folder in an NTFS file system: the filesystem doesn't support it or, at least, not the linux way. Also you CAN'T have your home folder on an NTFS filesystem. NTFS isn't case sensitive, doesn't support permisions and you can't make simlinks...

and, to finish, IT IS PROPIETARY CRAP.

---

### Post by stchman on 2007-05-04
> **NIKOSHIBA said:**
> hey there,
read and write going well.
Problem: every folder i make on ntfs partition owned by root, although i can create and delete it. i tryed to ```
chown username:users /mountpoin
``` but it doesn't work!!! owner and group are still root. it is irritating because i'm trying to export my /home to much larger and shared ntfs partition, but because of this ownership issue i get error message during login. Although afterwords everything going well.
How do i change ownership and group? 
plz help

Follow my procedure yo mount NTFS partitions under Ubuntu.  Make sure you have ntfs-3g installed:

sudo apt-get install ntfs-3g

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

This should help you.

---

