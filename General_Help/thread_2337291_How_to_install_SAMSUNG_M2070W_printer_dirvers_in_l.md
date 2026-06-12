---
title: "How to install SAMSUNG M2070W printer dirvers in linux"
date: 2016-09-16
forum: General Help
---

### Post by indre193 on 2016-09-16
Hello, could you tell me, how to install samusung M2070W printer drivers to linux. I  downloaded drivers from samsung (name ULD_v1.00.29.tar.gz). Thank you

---

### Post by howefield on 2016-09-16
Thread moved to the "*General Help*" forum.

What is inside the zipped tarball that you have downloaded, any readme files ?

I'd also recommend this forum.. [http://www.bchemnet.com/suldr/forum/index.php](http://www.bchemnet.com/suldr/forum/index.php)

---

### Post by indre193 on 2016-09-16
inside the zipped tarball are: folders (names "i386" and "noarch" and "x86_64" ), files: "install.sh" "install-printer.sh" "install-scanner.sh" "uninstall.sh" "uninstall-printer.sh" and "uninstall-scanner.sh" and any read me files.

---

### Post by howefield on 2016-09-16
Ordinarily you would extract the zipped tarball and navigate to the extracted folder then start the install script. I'd check the version number of the driver that you have, there appears to be a newer version available, but I may be wrong.

Lets, say you extract the download to the Downloads folder, you could

```
cd ~/Downloads
```
```
sudo sh install.sh
```

You may need to do the same with the other install files.

---

