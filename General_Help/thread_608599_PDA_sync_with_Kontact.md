---
title: "PDA sync with Kontact"
date: 2007-11-10
forum: General Help
---

### Post by blackfire on 2007-11-10
Hello everybody
 after days of searching, I finally managed to sync my pda with (K)ubuntu Gutsy.
I've got an i-mate pda2k, a win-running pda.
Under Dapper I was able to sync everything ok, using the usual synce / raki / synce-kde combo - I'm a Kontact user obviously. Under Feisty I lost my calendar. Under Gutsy I was not able to sync anything due to the infamous Wrong Library Type problem.
Since I was not able to find any solution, I resolved to do it myself.
I don't have a full log of everything I installed, but there are plenty of tutorials (for feisty) about installing synce, synce-kde, kitchensync, raki and the other stuff.
But that's not enough. I had to download  the feisty package of kitchensync, 
```

http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fk%2Fkdepim%2Fkitchensync_3.5.6-0ubuntu6_i386.deb&md5sum=c352ac1ec1bcb430fabbf8ae1eca8e3f&arch=i386&type=main,

```
 
and manually copy the libsync2, libkonnector, libkcalconnector and libmultisynk to /usr/lib directory. Those files are missing from the new packages, I don't have a clue why (so if you know, i'm just curious).

This will solve the "contacts" part.

About, the calendar: i ended up using another combo:

GooSync + gcaldaemon in http mode.
This is a rather standard setup.

Hope this will help, I've lost hours on this stuff.

---

