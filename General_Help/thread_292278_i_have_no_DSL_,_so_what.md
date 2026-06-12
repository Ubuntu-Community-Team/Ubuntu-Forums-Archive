---
title: "i have no DSL , so what ??"
date: 2006-11-03
forum: General Help
---

### Post by atk8877 on 2006-11-03
hai there ..
i have no DSL , but really i like Ubuntu , so i got conexant driver 4 edgy 6.10 , i installed it , but when i tried 2 connect the net i failed , so i tried 2 instal gnome-ppp it gave this 2 me :
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
and yas , i have installed c complier and gcc , so what ??

---

### Post by taurus on 2006-11-03
You need to install build-essential before you can compile or build anything from source!!!  The good news is it is on your CD so insert the CD into the drive, open a terminal with Applications -> Accessories -> Terminal, and type

```

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

```

---

