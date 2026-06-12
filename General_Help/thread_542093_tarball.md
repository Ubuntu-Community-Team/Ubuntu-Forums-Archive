---
title: "tarball"
date: 2007-09-03
forum: General Help
---

### Post by robeec on 2007-09-03
i dl-ed the driver for quick cam. since i mainly have used the package managers to install files, i am clueless on how to install a tarball on a debian system. i know i have to either use a root shell or 'sudo' but after that i'm lost. i'm gonna post my query on the ubuntu forum but i figured you might know. do i have to convert the file?
thanks,
robby
i have qc-usb-0.6.6.tar.gz on my desktop.

---

### Post by taurus on 2007-09-03
Applications -> Accessories -> Terminal
```
cd ~/Desktop  <-- assuming you saved the download theres.
tar xvzf qc-usb-0.6.6.tar.gz
cd qc-usb-0.6.6
sudo aptitude upate
sudo aptitude install build-essential checkinstall <-- you need the build-essential before you can build something from source.
./configure
make
sudo make checkinstall
```

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by robeec on 2007-09-03
thanks buddy! you rule!

---

