---
title: "How do I  create a .deb package from a tarball?"
date: 2007-02-08
forum: General Help
---

### Post by zakhooi on 2007-02-08
Hi,

I have a nice tarball (<file>.tar.gz) which installs fine with this procedure:
./configure
make
sudo make install

Now I like to make a .deb from this package.

Can anyone explain to me how to do this?

thanks in advance

---

### Post by Stemp on 2007-02-08
Install **checkinstall** package and then :
```

./configure
make
sudo checkinstall
```

---

### Post by shailender0435 on 2008-03-08
i installed clamav from source code
and i was asked for the dependencies 
> libgmp3 libgmp3-dev
groupadd
i installed the dependencies ....
through checkinstall script i have prepared a deb package ....
and my doubt is 
for next time if i install the clamav from the deb package which i have prepared will i get the dependencies with that or should i install the dependencies again?

apologize me for my poor english...

---

### Post by SoulSmasher on 2008-03-21
afaik, no need to reinstall dependencies later..

worked for me, made a deb package for conky, thanks :)
[URL="http://rapidshare.com/files/101351830/conky_1.4.9-ubuntutr1-1_i386.deb"]
http://rapidshare.com/files/101351830/conky_1.4.9-ubuntutr1-1_i386.deb[/URL]

---

