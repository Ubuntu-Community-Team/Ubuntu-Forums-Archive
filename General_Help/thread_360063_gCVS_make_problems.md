---
title: "gCVS make problems"
date: 2007-02-12
forum: General Help
---

### Post by smacd on 2007-02-12
Not sure where else to go with this question.

I'm trying to set up gCVS-1.0 on my system (Xubuntu Edgy). I can run ./configure fine (so I assume that I have all the dependencies set-up -- finally). however, I'm getting a strange problem with the make file. Can anyone help me with this? I'm completely clueless...

> 
owner@laptop:~/programs/gcvs-1.0$ make
make  all-recursive
make[1]: Entering directory `/home/owner/programs/gcvs-1.0'
Making all in common
make[2]: Entering directory `/home/owner/programs/gcvs-1.0/common'
source='AboutDlg.cpp' object='AboutDlg.o' libtool=no \
        depfile='.deps/AboutDlg.Po' tmpdepfile='.deps/AboutDlg.TPo' \
        depmode=gcc3 /bin/bash ../depcomp \
        g++ -DHAVE_CONFIG_H -I. -I. -I.. -I../gcvs -I../gcvs/src -I/. -I../cvstree -I../rf  -Wall -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DqUnix -DqGTK -INONE -DqCvsDebug=0  -g -O2 -c -o AboutDlg.o `test -f 'AboutDlg.cpp' || echo './'`AboutDlg.cpp
../rf/ustr.h:178: error: extra qualification ‘UStr::’ on member ‘operator+=’
../rf/ustr.h:180: error: extra qualification ‘UStr::’ on member ‘operator+=’
../rf/ustr.h:182: error: extra qualification ‘UStr::’ on member ‘operator+=’
../rf/ustr.h:184: error: extra qualification ‘UStr::’ on member ‘operator+=’
make[2]: *** [AboutDlg.o] Error 1
make[2]: Leaving directory `/home/owner/programs/gcvs-1.0/common'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/owner/programs/gcvs-1.0'
make: *** [all] Error 2


---

### Post by tbroderick on 2007-02-12
Not sure about your error, but gcvs1.0 is in the repos.
```
sudo apt-get install gcvs
```

---

### Post by smacd on 2007-02-12
hmm, when i tried
> sudo apt-get install gcvs
I get the response
> E: Couldn't find package gcvs

---

### Post by tbroderick on 2007-02-12
Do you have universe enabled?

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gcvs&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gcvs&searchon=names&subword=1&version=all&release=all)

---

