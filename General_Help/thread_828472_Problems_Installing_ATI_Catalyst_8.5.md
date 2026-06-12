---
title: "Problems Installing ATI Catalyst 8.5"
date: 2008-06-13
forum: General Help
---

### Post by liam848 on 2008-06-13
I'm trying to install the ATI Catalyst drivers version 8.5 by following the instructions [here]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide"). I'm getting a really strange problem when I try to generate the deb package. 

```
Generating package: Ubuntu/8.04
Resolving build dependencies...
./packages/Ubuntu/ati-packager.sh: 311: sh -c '/usr/sbin/synaptic --set-selections --non-interactive --hide-main-window < /tmp/filepT902f': not found
Unable to resolve  can't parse dependency ooobasis30-en_us-res
 can't parse dependency ooobasis30-en_us-help
 can't parse dependency ooobasis30-en_us
 can't parse dependency ooobasis30-en_us-base
 can't parse dependency ooobasis30-en_us-math
 can't parse dependency ooobasis30-en_us-calc
 can't parse dependency ooobasis30-en_us-onlineupd
 can't parse dependency ooobasis30-en_us-impress
 can't parse dependency ooobasis30-en_us-draw
 can't parse dependency ooobasis30-en_us-writer.  Please manually install and try again.
Removing temporary directory: fglrx-install.jU9887
```

It seems to be calling OpenOffice as a dependency :confused:. I don't really see why this is happening, and would greatly appreciate it if someone could enlighten me.

---

### Post by crazyn3wf on 2008-07-08
Same thing here, but it does complete the build and debs are OK.
```
$ ./ati-driver-installer-8-6-x86.x86_64.run --buildpkg Ubuntu/hardy
Created directory fglrx-install.Y15757
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.501..............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/hardy
Resolving build dependencies...
Unable to resolve  can't parse dependency ooobasis30-en_us-res
 can't parse dependency ooobasis30-en_us-help
 can't parse dependency ooobasis30-en_us
 can't parse dependency ooobasis30-en_us-base
 can't parse dependency ooobasis30-en_us-math
 can't parse dependency ooobasis30-en_us-calc
 can't parse dependency ooobasis30-en_us-onlineupd
 can't parse dependency ooobasis30-en_us-impress
 can't parse dependency ooobasis30-en_us-draw
 can't parse dependency ooobasis30-en_us-writer.  Please manually install and try again.

```

---

### Post by adben on 2008-09-17
Of course you need to dl a new file when you can patch it with one sed line  Verify MD5 sum, it will match!

Before:
378ed98c6b8e30eba1614eb5f2ba0696 *ati-driver-installer-8-5-x86.x86_64.run

Fix:
```
signature="8260783741db03d98508ca69a1795f0e:ba4e4c0e72f633e1b53dfb5bc0546f38b652410502f6428dcc28fe5999486f37:e0014c5275b833bcb23aac5f924a3a3fe0554b5327b936bbe638ff5d971f6c36e0564d0575ea33ecb53aac5f954b676ae1034a0f27be36e0bc31fe51971f6c39"
sed -i 's/\(signature=\).*/\1"'$signature'"/' ati-driver-installer-8-5-x86.x86_64.run
```

After:
303a7c2c5a42f21cb92692cf77c83052 *ati-driver-installer-8-5-x86.x86_64.run

---

