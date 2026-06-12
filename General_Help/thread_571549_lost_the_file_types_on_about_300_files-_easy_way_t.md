---
title: "lost the file types on about 300 files- easy way to use the terminal to fix it?"
date: 2007-10-09
forum: General Help
---

### Post by onesojourner on 2007-10-09
I have about 300 files that some how lost the file types on the end of them.( ex. .bmp) 

I know there has to be an easy way to use the terminal to add the file types back to them with out having to manually go through and rename every single file.

thanks in advance.

---

### Post by nikhilk on 2007-10-09
Copy this
```

#!/bin/bash

for file in <path to files>/*; do
    mv "$file" "$file.bmp"
done

``` in a file and run it as ```
bash <filename>
```

Forgot to state the following assumption
> **thirddeep said:**
> That is assuming ALL the files is said folder is of the same type :-)
Thanks thirddeep.

---

### Post by thirddeep on 2007-10-09
That is assuming ALL the files is said folder is of the same type :-)

Thd.

---

### Post by onesojourner on 2007-10-09
ok that almost worked but any file that has a space in it was not effected. And most of them have a  space in them.

---

### Post by bodhi.zazen on 2007-10-09
Well, first in linux you do not need to use the .bmp ...

Second, 

```
find . -type f -exec mv '{}' '{}'.bmp \;
```

---

### Post by onesojourner on 2007-10-09
ok that worked but some how I have added .smc to every single file in my home directory. how can I undo that?

---

### Post by bodhi.zazen on 2007-10-09
```
rename 's/.smc/\ /g' *
```

---

### Post by onesojourner on 2007-10-09
that change the things in my home folder but all the files on the desktop remain with a .smc

---

### Post by bodhi.zazen on 2007-10-09
LOL

cd ~/Desktop
rename 's/.smc/\ /g' *

---

### Post by onesojourner on 2007-10-09
here is what I get with that command

Unknown option: {
Unknown option: m
Unknown option: i
Unknown option: i
Unknown option: o
Unknown option: a
Unknown option: .
Unknown option: o
Unknown option: r
Unknown option: g
Unknown option: }
Unknown option:  bbl.mp3.smc
Usage: rename [-v] [-n] [-f] perlexpr [filenames]

---

### Post by onesojourner on 2007-10-10
the .smc seems to have messed up several programs. Firefox has been reset. ect..

---

