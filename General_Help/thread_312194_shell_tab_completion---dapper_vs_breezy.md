---
title: "shell tab completion---dapper vs breezy"
date: 2006-12-04
forum: General Help
---

### Post by rgrig on 2006-12-04
The shell tab completion behaves differently on two computers with dapper: one upgraded from breezy and one installed from scratch. In a directory with files a.ps and a.pdf I type "acroread a.p<TAB>". On the system installed form scratch this completes "df"; on the upgraded system a second <TAB> gives a list with two choices.

How can I make the upgraded system behave like the one installed from scratch (that is, be extension sensitive)?

---

### Post by girishv on 2006-12-04
most probably, you have installed bash_completion on your earlier system. Try installing this on your second installation too. bash completion is aware of the programs and corresponding extensions.

girish

---

### Post by rgrig on 2006-12-18
There is no bash_completion package as far as I can tell.

```

rg@rg-ucd:temp$ sudo apt-get install bash_completion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bash_completion

```

---

### Post by rgrig on 2006-12-20
If I source the file /etc/bash_completion it works. I guess I'll just add this to ~/.bashrc.

---

