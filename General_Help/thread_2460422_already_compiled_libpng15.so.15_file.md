---
title: "already compiled libpng15.so.15 file"
date: 2021-04-09
forum: General Help
---

### Post by ubuntini2 on 2021-04-09
Is anyone aware of anyway I can download the already compiled libpng15.so.15 file?

 I am missing it for a specific application.

---

### Post by Xian on 2021-04-09
You'll need to compile it yourself .... sorry. 

[https://sourceforge.net/projects/libpng/files/libpng15/older-releases/1.5.15/](https://sourceforge.net/projects/libpng/files/libpng15/older-releases/1.5.15/)

```
[FONT=monospace]wget https://sourceforge.net/projects/libpng/files/libpng15/older-releases/1.5.15/libpng-1.5.15.tar.gz
[/FONT]tar -zxvf ./libpng-1.5.15.tar.gz
[COLOR=#397300]cd[/COLOR] libpng-1.5.15
./configure --prefix=/usr/[COLOR=#397300]local[/COLOR]/libpng
make check
sudo make install 
[FONT=monospace]make check[/FONT]
```

---

