---
title: "help writing  a bash script."
date: 2008-05-13
forum: General Help
---

### Post by pixeldotz on 2008-05-13
been a while since i posted :)

here's the scenario.

i have my laptops hdd partitioned as such

10GB - damn small linux not
40GB - xp
40GB - ubuntu studio

i have grub dualbooting xp and ubuntu studio and have been running this setup for a little over a year now.

here's what i've done after a complete reinstall of xp and ubustu, i used this guide
[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore]("http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore")

to create two tar files on my 10GB partition.
xp.tgz
ubustu.tgz

in my grub listing i have the very last menu item listed as
recovery partition and use the same guide to untar those files into their respective partition and so far everything has been awesome and works perfectly.

now, i can write the bash script that untars them automatically but i have to hardcode WHERE to untar them too.

can anyone help me write the lines that would ASK where the tar file is located and WHERE i want to untar it too?

dsln is perfect for this since it's the easiest and smallest to install to my hdd as a recovery tool to just use tar (i'm sure there are other smaller txt only distros that would satisfy this need but dsln was the easiest for me)

thanks for any help.

---

### Post by Monicker on 2008-05-13
Here is something real basic.  No checking of input or anything fancy:
```

#!/bin/bash

read -p "Where is the tar file to be extracted? " fileloc

echo
read -p "Where would you like to extract this file? " extractloc

echo

echo "File to be extracted: $fileloc"
echo "Extract location for file: $extractloc"
```

---

### Post by pixeldotz on 2008-05-13
thanks! that helped with everything.

i just added 

```
tar xvpfz $fileloc -C $extractloc
```

to the bottom of your script and everything came out awesome.

so now i have a full blown restore partition on my laptop. dsln is giving me a hard time with mounting ntfs as rw so i might just go with very small xubuntu install on there, or maybe even keep it clean and use a livecd to boot to that partition when i need to restore.

again, thanks for the help!

---

