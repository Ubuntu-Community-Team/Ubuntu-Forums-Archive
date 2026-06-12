---
title: "[SOLVED] NERO (game) - how do you install?"
date: 2006-12-23
forum: General Help
---

### Post by altonbr on 2006-12-23
[http://doc.gwos.org/index.php/NERO](http://doc.gwos.org/index.php/NERO) // [http://www.nerogame.org/](http://www.nerogame.org/)

Can someone please inform me how to install this game?

```
tar -zxvf NERO_Linux_101.tgz
cd nero_101_ubuntu
./configure
make
make install
```

The above doesn't work. It says that configure isn't a directory... and there's no README and no installation help in the documentation.

---

### Post by iamhugeinjapan on 2006-12-23
Try running nero.bin in the nero_101_ubuntu folder.

---

### Post by iamhugeinjapan on 2006-12-23
Also looking at the forums it looks like the Windows version will run with Wine anyway. So if you have no luck with the Linux install, try that one.

---

### Post by altonbr on 2006-12-29
Running ./nero.bin in "nero_101_ubuntu" returns:

> ./nero.bin: symbol lookup error: ./nero.bin: undefined symbol: X11_KeyToUnicode

I'll try the Windows installer in Wine, thanks.

---

