---
title: "two kubuntu edgy questions, please help"
date: 2006-12-21
forum: General Help
---

### Post by maddbaron on 2006-12-21
I installed Gaim when I upgraded a while back. I have no sound on my notifications. Does anyone know how to fix that? Its gaim beta 4 i think.

Also is there a command line code that can be used to kinda refresh the system like how you refresh the desktop? Sometimes when i am running Firefox it hogs my memory and if i am running with another internet using program i get lock ups and i have to refresh b/c it uses about 100 percent of my cpu, is there a code that i can use to refresh without having to reboot?

---

### Post by shanepardue on 2006-12-22
1) The gaim issue may be fixable by upgrading to the latest gaim (beta 5). I remember having 
that same problem with a version of gaim awhile back. here's the repo for beta 5...

```
#Debuntu Repo
deb  [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse
```

and the key
```
cd ~
wget http://repository.debuntu.org/GPG-Key-chantra.txt
sudo apt-key add GPG-Key-chantra.txt
rm GPG-Key-chantra.txt
```

2) I'm not sure what you mean by a "refresh", but Ctrl+alt+backspace may be up your alley. 
Give it a whirl when you don't have any unsaved projects open.

---

