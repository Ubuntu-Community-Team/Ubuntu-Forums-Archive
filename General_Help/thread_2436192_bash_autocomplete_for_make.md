---
title: "bash autocomplete for make"
date: 2020-02-01
forum: General Help
---

### Post by memilanuk on 2020-02-01
So...

I have an account on an online IDE/sandbox (ide.cs50.io) that uses Ubuntu 18.04.3 LTS.  In that particular environment, typing ```
make fi<tab>
``` will autocomplete to ```
make filename
```.  

I also have a Chromebook running crostini, which by default runs Debian 10 (Buster).  In that environment, typing ```
make fi<tab>
``` yields nothing.  As far as I can tell, tab autocompletion in the shell on Debian only autocompletes the command name itself i.e. 'make', but not the command options.  I'm trying to figure out how to configure the environment on the CB like on the sandbox.  

Both have the 'bash-completion' package installed, and near as I can tell, the config files '/etc/profile.d/bash-completion' and '/usr/share/bash-completion/completions/make' seem literally identical.  

Does anyone here have some fluency with both systems that can help me out with this?

Thanks!

---

