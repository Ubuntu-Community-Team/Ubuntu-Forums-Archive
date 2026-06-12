---
title: "Running a Linux program from a python script that's running on Windows"
date: 2021-11-30
forum: General Help
---

### Post by zivlang on 2021-11-30
I'm using WSL for this purpose. I run the command
```
Popen(['wsl', '/tmp/docker-desktop-root/mnt/host/c/Users/user/ensembl-vep/vep\n'], stderr=STDOUT).stdout
```
from the python script to run a Linux program called "ensembl-vep". Unlike  when I run the command in "Ubuntu on Windows", when I run it from the  python script I get the following error message: > env: can't execute 'perl': No such file or directory.

I tried adding the environment variable from "Ubuntu on Windows" from the python script and got the same error.

Is there a way to solve this issue?

---

### Post by TheFu on 2021-12-01
I know ZERO about WSL. Sorry.  

Which perl is being called, the Windows one or the Linux one?
Is strawberry perl installed in Windows?
perl is part of standard Ubuntu.

I don't use Docker, but if the script is inside a docker container, I wouldn't think that anything not included in that container would be used.

Seems overly complex.  Script everything inside WSL (or a real Linux install), then use ssh from Windows to call that single script. I suppose if there must be multiple parts called by Windows, you could write an output file for each stage of the process when on Linux we'd typically use pipes instead to pass the output from 1 command to the next command.  It is very common to do that in all Unix-like OSes.

Or am I missing the point entirely? That is very likely too.

---

