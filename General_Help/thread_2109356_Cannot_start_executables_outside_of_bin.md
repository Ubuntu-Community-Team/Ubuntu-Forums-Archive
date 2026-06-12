---
title: "Cannot start executables outside of /bin"
date: 2013-01-27
forum: General Help
---

### Post by _nikolaos on 2013-01-27
After my upgrade to Ubuntu 12.04 from 10.04 (I have to update my forum profile), I have a strange problem with the terminal.

Scripts that they start from top line **#!/bin/sh** refuse to start unless my working directory is $HOME/bin (HOME=/home/user) or /usr/bin or /bin or any similar. The same seems to go with programs compiled by gcc, a.out is executable but is denied permission to execution.

I have checked thoroughly for any chmod or chown or chgrp mistakes. I know that usually there are some root owners because I "sudo" often, so I should make changes to the files, but this is not my case. Everything is allright.

I noticed that typing "sh" before the script name, instead of "./" works things out. But it is not convenient, because for example, a package compilation can go wrong:

./configure --> displays "permission denied"
sh configure --> goes on but when testing the gcc compiler

```
checking whether we are cross compiling... configure: error: in `/home/user/area/alacarte':
configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details
```

and "config.log" just mentions "exit 1" at the bottom line. Of course there's no cross-compilation.

The file /bin/sh is a symlink to /bin/dash. I changed it to /bin/bash, but nothing different happened, so I restored it.

Do these files /bin/bash and /bin/dash make check whether they are going to execute a file at a "bin"-like folder, supposed to be for executables?

Is it the new version upgrade that changed something?

Anyway, this is a persisting and annoying feature that I need to bypass. I know this is not a part of a good habit to keep executables out of "bin" folders, but I want my choices.

Please help me fix this.

---

