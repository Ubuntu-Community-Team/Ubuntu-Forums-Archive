---
title: "problem installing sunbird"
date: 2007-06-29
forum: General Help
---

### Post by seshomaru samma on 2007-06-29
I saw on Slashdot that there is a new sunbird for Linux
I downloaded the tar.gz from Mozilla's website untared it and found the following files there :
```
chrome              libfreebl3.so    libsoftokn3.so          removed-files
components          libmozjs.so      libssl3.so              res
defaults            libnspr4.so      libxpcom_compat.so      run-mozilla.sh
dependentlibs.list  libnss3.so       libxpcom_core.so        sunbird
extensions          libnssckbi.so    libxpcom.so             sunbird-bin
greprefs            libplc4.so       libxpistub.so           updater
icons               libplds4.so      LICENSE                 updater.ini
js                  libsmime3.so     mozilla-xremote-client  updates
libfreebl3.chk      libsoftokn3.chk  README.txt              xpicleanup
```
the README just sent me back to the downloading page and when i run 
```
sh ./run-mozilla.sh

```
i get 

```
run-mozilla.sh: Cannot execute .
```
i tried to chmod a+x it but i still get 'cannot execute'

any suggestions?

---

### Post by Brucevdk on 2007-06-29
How about:
```

./sunbird

```

---

### Post by seshomaru samma on 2007-06-29
take makes sense ,
i should have tried that 
however i get:
```
sesho@desktop:~/Desktop/sunbird$ ./sunbird
./run-mozilla.sh: line 131: 22338 Segmentation fault      "$prog" ${1+"$@"}
```

---

