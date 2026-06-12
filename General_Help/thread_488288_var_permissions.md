---
title: "var permissions"
date: 2007-06-30
forum: General Help
---

### Post by American_Outcast on 2007-06-30
I am new to permissions. I understand now, after the fact, what, for ex., drwxr-xr-x root mysql means. r=read, w=write, x=execute, - =none (I am not sure what t means yet.)

First letter tells you if it is a directory. the following three are owner permissions, next three are group permissions and the last three are other and root would be owner, mysql would be group

Now what I need to do is fix my /var/ directory, sub-directories and files.

I have apache2, mysql, php5, etc, set up. I am going through this right now and making sure the permissions are set up correctly. Someone on another forum gave me a copy of most of their /var/ permissions list, with ls -ld, but it is not from an Ubuntu system. Can someone share theirs with me so I have a better model to go by? I am using Ubuntu 7.04

(I could just list my /var/ permissions here but I would rather do this myself and not just have someone read the list and tell me what to do, its the only way I can learn.)

Thanks in advance.

---

### Post by arvevans on 2007-06-30
Pull up a terminal screen and at the prompt enter "man chmod".  This will show you a user manual for the "chmod" command.

[INDENT]When using man pages, you use arrow keys to navigate and "q" to exit the page viewer.[/INDENT]

Reading over how this command works should give you a good idea of how directory and file permissions are managed.
_._

---

