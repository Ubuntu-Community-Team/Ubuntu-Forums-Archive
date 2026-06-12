---
title: "Runing iFolder client on Gusty"
date: 2007-11-02
forum: General Help
---

### Post by ikus060 on 2007-11-02
I'm trying to install and run iFolder3.4 on Gusty.
At this time I got this files :
```
ifolder3-3.4.6214.1.tar.gz
nautilus-ifolder3-3.4.6214.1.tar.gz
simias-1.4.6214.1.tar.gz
```
from this adresse [http://forgeftp.novell.com/ifolder/client/3.4/current/src/](http://forgeftp.novell.com/ifolder/client/3.4/current/src/)

I can compile ifolder and simias without any problem. When I try to run ifolder via "ifolder" command line I receive this error :
```
[: 7: ==: unexpected operator
Error: Cannot start the local web services.
Error: The Simias process failed to initialize.
       Use the command line switch --showconsole to view the error.
```

If I execute "simias --showconsole" I don't get any more information regarding the error. I check in ~/.local/share/simias/ for any clue of the problem. There's nothing.

Thank for your help

Any one got it working on gusty ??

---

