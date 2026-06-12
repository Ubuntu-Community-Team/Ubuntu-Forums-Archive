---
title: "usplash Help"
date: 2007-07-24
forum: General Help
---

### Post by iamadam on 2007-07-24
Hi. I'm trying to create a custom usplash image but I'm having no joy. I've created 3 different indexed PNG images, sizes of 640x480, 800x600, 1024x768 with pallete sizes varying from 16 to 256. I am then running

```
pngtobogl my_usplash.png > usplash-artwork.c 
gcc -Os -g -I/usr/include/bogl -fPIC -c usplash-artwork.c -o usplash-artwork.o
gcc -shared -Wl,-soname,usplash-artwork.so usplash-artwork.o -o my_usplash.so
```

which works fine. Then I symlink it:

```
 sudo cp my_usplash.so /usr/lib/usplash/my_usplash.so
 sudo ln -sf /usr/lib/usplash/my_usplash.so /usr/lib/usplash/usplash-artwork.so
```

Then run

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

but on reboot, it fails to load and just goes to the console. Any suggestions or link to a decent guide would be great! I used this guide to get started [http://doc.gwos.org/index.php/Change_Usplash](http://doc.gwos.org/index.php/Change_Usplash) but had no joy with the images supplied there either.

I'm running Feisty and have my VGA mode set to 1024x768 btw. Not sure if that matters?

---

### Post by BOBSONATOR on 2007-07-24
use this to help you.

[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)

---

