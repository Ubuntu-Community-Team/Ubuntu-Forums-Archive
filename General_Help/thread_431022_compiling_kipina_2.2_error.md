---
title: "compiling kipina 2.2 error"
date: 2007-05-02
forum: General Help
---

### Post by tempo500 on 2007-05-02
hi,

can someone help me with this? i am trying to compile kipina 2.2 on feisty 32bit and did it befor! but somhow i am stuck here, exectuing the make command

make[2]: Entering directory `/home/phil/kipina-0.2.2/data'
Making all in images
make[3]: Entering directory `/home/phil/kipina-0.2.2/data/images'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/phil/kipina-0.2.2/data/images'
make[3]: Entering directory `/home/phil/kipina-0.2.2/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/phil/kipina-0.2.2/data'
make[2]: Leaving directory `/home/phil/kipina-0.2.2/data'
Making all in po
make[2]: Entering directory `/home/phil/kipina-0.2.2/po'
file=`echo fi | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file fi.po
/bin/sh: -o: not found
make[2]: *** [fi.gmo] Error 127
make[2]: Leaving directory `/home/phil/kipina-0.2.2/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/phil/kipina-0.2.2'
make: *** [all] Error 2

---

### Post by pixelstuff on 2007-06-11
hello! have you been succesfull? I get in all folders   "No targets specified and no makefile found.  Stop."   ./configure seems to work, at least theres no error but also no output :(

---

### Post by tempo500 on 2007-06-24
no. but it worked like always on ubuntu64bit.... dont know the difference to 32bit... phil

---

