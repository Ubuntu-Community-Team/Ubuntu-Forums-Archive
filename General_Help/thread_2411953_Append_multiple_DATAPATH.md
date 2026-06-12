---
title: "Append multiple DATAPATH"
date: 2019-02-06
forum: General Help
---

### Post by amivaleo on 2019-02-06
Hi!

I need to export several datapaths in my bashrc.

This is what I do:
```
export $DATAPATH = "$HOME/folderA:$HOME/folderB:$HOME/folderC"
```
But it doesn't work. If I try to run one of the software that uses folderA or folderB or folderC, they all crash because they can't find their folders/datapaths.

My $PATH variable is set in a very similar way, with even more folders, and it works fine.
How should I set $DATAPATH instead?


Thank you!

---

### Post by dragonfly41 on 2019-02-06
This is how I concatenate multiple paths in my ~/.profile file 

```
export $DATAPATH=$HOME/folderA
export $DATAPATH=${DATAPATH}:$HOME/folderB
export $DATAPATH=${DATAPATH}:$HOME/folderC
```

---

### Post by Holger_Gehrke on 2019-02-06
That
```
export $DATAPATH = "$HOME/folderA:$HOME/folderB:$HOME/folderC"
```
won't work, for several reason.
[LIST=1]
[*]The shell isn't PHP. The '$'-sign introduces parameter substitution, so the value of DATAPATH is put in place of $DATAPATH. 
[*]There must not be anything between the variable name and the '=' sign. 
[*]DATAPATH is not a standard variable. There are PATH, CD_PATH, MAIL_PATH, and LD_LIBRARY_PATH but no DATAPATH. Unless the documentation of a program tells you that it expects that variable and will interpret it's content as a list of directories to search for data, setting this will not have the kind of effect you seem to expect. 
[/LIST]
So - disregarding the third point - the line should read
```

export DATAPATH="~/folderA:~/folderB:~/folderC"

```
('~' is another shell-shortcut: ~USER is replaced with the home-directory of USER; if no USER is given, the home-directory of the current user is substituted.)

Holger

---

### Post by sisco311 on 2019-02-06
Tile expansion only applies when '~' is unquoted.  See: BashPitfalls #26 (link in my signature).

---

