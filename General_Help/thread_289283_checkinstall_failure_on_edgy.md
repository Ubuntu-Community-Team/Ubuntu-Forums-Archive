---
title: "checkinstall failure on edgy"
date: 2006-10-30
forum: General Help
---

### Post by mewkiss on 2006-10-30
I have downloaded the newest xscreensaver tarball (5.01) from jwz.org. I've always had good luck building Jamie's tarballs of xscreensaver and have previously successfully used the *checkinstall* script to create and install a deb. This time around I managed to get past *./configure* and *make *but when I got to the "sudo checkinstall -D make install" part I got this error: 
```

[B]checkinstall: 54: Syntax error: "}" unexpected.
[/B] 
```Looking at the checkinstall script I find the following function:
```

function ckversion {
   echo
   echo "checkinstall $CHECKINSTALL_VERSION, Copyright 2001 Felipe Eduardo Sanchez Diaz Duran"
   echo "           This software is released under the GNU GPL."
 }

```with that closing right curly bracket sitting on the offending line number 54. The function *does *execute and print the version number message to the console before choking on the closing bracket. Everything looks in order and the script is in unedited 'out of the box' condition which never threw this error before. The only thing that has changed is my upgrade to Edgy Eft from Dapper. I know I could just do a 'make install' but I would naturally prefer an integrated installation from a deb.

So...anybody know what's going on here?

---

### Post by mewkiss on 2006-11-04
FWIW - I got this to work simply by a 'shot in the dark' solution of using the full path to checkinstall (/usr/bin/checkinstall) at the command line. I don't understand why that worked...but it did. It was worth the trouble just to have the new xscreensaver hack "GLSchool". :cool:

---

### Post by Blutack on 2006-11-04
As long as you are in the directory with the configure file in...
type

./configure
sudo checkinstall

and that should do the trick.  I have never used make install after the command checkinstall - checkinstall makes and installs all itself.
I suspect that your /usr/bin trick worked because you missed of some of the stuff after checkinstall!

---

### Post by mewkiss on 2006-11-05
> **Blutack said:**
> As long as you are in the directory with the configure file in...
type

./configure
sudo checkinstall

and that should do the trick.  I have never used make install after the command checkinstall - checkinstall makes and installs all itself.
I suspect that your /usr/bin trick worked because you missed of some of the stuff after checkinstall!

Duly noted Blutack. Thanks for the input.

---

