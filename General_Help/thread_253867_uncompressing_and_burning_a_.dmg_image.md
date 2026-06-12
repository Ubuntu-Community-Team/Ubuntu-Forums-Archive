---
title: "uncompressing and burning a .dmg image"
date: 2006-09-09
forum: General Help
---

### Post by Patrick-Ruff on 2006-09-09
hey all, I've been trying to open a .dmg file on windows for quite a while, the maker of this dvd compressed it like mad, so its a compressed .dmg file, does anyone know of any sort of method to open/decompress/convert this file? Linux seems far more likely then window's, I've tried everything on windows, no dice, and I don't have a Apple computer handy either.


thanks to all who reply.

---

### Post by Patrick-Ruff on 2006-09-09
just an add on to the thread, my friend told me that the .dmg is compressed with bz, so its a bz compressed dmg. if you know of an app that can open it or may be able to, PLEASE suggest it!


thanks

---

### Post by Patrick-Ruff on 2006-09-09
someone here should have a slight idea....

---

### Post by maxpower on 2006-09-26
You may want to try using google, I found the following article as the first result for a "dmg linux" search.

[http://baghira.sourceforge.net/dmg.htm](http://baghira.sourceforge.net/dmg.htm)

mAx

---

### Post by flouran on 2008-07-19
The only way you can mount a dmg with the command, sudo mount -t hfsplus -o loop /path/to/dmg /mount/point, is to decompress it first into an img file.

In order to decompress a dmg, then mount it, download dmg2img from [http://vu1tur.eu.org/tools/download.pl?dmg2img.tar.gz](http://vu1tur.eu.org/tools/download.pl?dmg2img.tar.gz)
Then, after saving the file, dmg2img in your home folder, open terminal, and run, tar -zxvf ./dmg2img.tar.gz, then run run, cd dmg2img, then once you are inside the dmg2img directory run, make all.

If everything goes okay, then you can decompress your dmg file by executing the command, ./dmg2img -i /path/to/inputfile.dmg -o /path/to/outputfile.img, and remember, you must be inside the dmg2img directory at all times in order to run the command listed above. Also, the img file needs to be in the same location as the original dmg file. And preferably, the img file should have the same name as the dmg file. After decompressing the dmg, run, sudo modprobe hfsplus, then if hfsplus is installed (if not, run sudo apt-get install hfsplus), run sudo mount -t hfsplus -o loop /path/to/outputfile.img /mount/point. To create the mount point, run mkdir -p /mount/point.

---

