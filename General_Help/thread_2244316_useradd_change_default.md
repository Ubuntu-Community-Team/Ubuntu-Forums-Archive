---
title: "useradd change default"
date: 2014-09-15
forum: General Help
---

### Post by BruceFulton on 2014-09-15
Ubuntu server, 14.04lts useradd is still documented (man page) to be able to change the default shell on adding new user with the -s switch, but this doesn't seem to be working on this version of Ubuntu server. 

$ useradd -D
...shows default shell of /bin/sh

$ useradd -D -s /bin/bash
...
then
$ useradd -D
...still shows default shell of /bin/sh

As far as I know, this has been working in previous versions of Ubuntu server. 
[ATTACH=CONFIG]256462[/ATTACH]

---

