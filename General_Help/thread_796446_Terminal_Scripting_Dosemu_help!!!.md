---
title: "Terminal Scripting Dosemu help!!!"
date: 2008-05-16
forum: General Help
---

### Post by WebWatch on 2008-05-16
I've been trying to create a shell script (shortcut) to run the following script in x-terminal which will change the mmap then launch my 16 bit program using dos emulator (couldn't get wine to work), then return the mmap security.

So far my .sh file contains

#!/bin/sh
sudo sysctl -w vm.mmap_min_addr=0
password
cd "/the/full/path/to/my/16bit/program/"
dosemu my_16bit_program.exe
sudo sysctl -w vm.mmap_min_addr=65536
password
exit

this will launch dosemu and then close it without launching my exe file

---

### Post by pointone on 2008-05-16
Change:

```
cd "/the/full/path/to/my/16bit/program/"
dosemu my_16bit_program.exe
```

...to:

```
dosemu /the/full/path/to/my/16bit/program/my_16bit_program.exe
```

---

### Post by emendelson on 2008-05-21
If those suggestions don't work, try adapting the suggestions here:

[http://www.columbia.edu/~em36/wpdos/linux.html#hotkey](http://www.columbia.edu/~em36/wpdos/linux.html#hotkey)

Remember that DOSEMU doesn't understand your Linux directory structure; you have to feed DOSEMU the path that will be visible to DOSEMU, maybe something like "C:\MYDIR\Myprog.exe"

---

