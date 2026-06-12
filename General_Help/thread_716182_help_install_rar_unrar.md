---
title: "help install rar unrar"
date: 2008-03-05
forum: General Help
---

### Post by zorlab on 2008-03-05
After trying apt-get install rar unrar,  as suggested in this forum I get no such file or directory,  universal repositories are open, and it appears this is no longer available. I did find a debian package and downloaded it to the desktop and untared it to the directory,"rar"

So......
from  the following site [http://imanhermawan.wordpress.com/2007/09/19/open-rar-file-or-extract-rar-files-under-linux-or-unix/](http://imanhermawan.wordpress.com/2007/09/19/open-rar-file-or-extract-rar-files-under-linux-or-unix/)

II tried the commands suggested, and have gotten no where. There has to be a better way!

I am sure many many have done this simply, but it alludes me. Please help.

I would also like to know how to install a package from and extracted dir, I tried make  ..  .  but I am pulling my hair  out thus far...

---

### Post by munkyeetr on 2008-03-05
Odd, I just ran the following line:
```
sudo apt-get install rar unrar
```

through both the Canadian and American repositories, and it installed through both no problem. So we know, at least, that it is still available.

---

### Post by stchman on 2008-03-05
> **zorlab said:**
> After trying apt-get install rar unrar,  as suggested in this forum I get no such file or directory,  universal repositories are open, and it appears this is no longer available. I did find a debian package and downloaded it to the desktop and untared it to the directory,"rar"

So......
from  the following site [http://imanhermawan.wordpress.com/2007/09/19/open-rar-file-or-extract-rar-files-under-linux-or-unix/](http://imanhermawan.wordpress.com/2007/09/19/open-rar-file-or-extract-rar-files-under-linux-or-unix/)

II tried the commands suggested, and have gotten no where. There has to be a better way!

I am sure many many have done this simply, but it alludes me. Please help.

I would also like to know how to install a package from and extracted dir, I tried make  ..  .  but I am pulling my hair  out thus far...

The packages rar and unrar are in the Multiverse repository.

The unrar-free package is in the Universe repository.  Make sure you have all your repositories enabled.

---

### Post by zorlab on 2008-03-05
OH!  sorry,  I thought the multi-verse was not free!  thanks  it installed

---

### Post by zorlab on 2008-03-05
installed fine but I  cannot "extract here", in GUI..
.:confused:

"An error occurred while extracting files":eek:

---

