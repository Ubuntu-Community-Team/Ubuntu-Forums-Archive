---
title: "Archive Manager rar problems"
date: 2005-08-27
forum: General Help
---

### Post by Cud on 2005-08-27
Hi folks, Im pretty much a newby, having a blast playing with Ubuntu. One thing I wanted to ask. Archive manager is not able to open some of the rar files I downloaded with amule. I get the error "could not open 'filename.rar'  Archive type not supported." Its wierd it doesn't happen with ALL rar files, just some. Is this just bad files, and if so is there aany way of knowing this BEFORE downloading??
Thanks a bunch..
Oh yeah I'm running hoary hedgehog 5.04 on a PC.

---

### Post by Tiede on 2005-08-27
```
apt-get install unrar
```
I had the same problem and solved it like so :)

---

### Post by RiTarDid on 2008-01-18
mine won't open password protected .rar's on the default xubuntu...perhaps that was the "corruption" in some of your files too :) .

---

### Post by gindc on 2008-04-16
you need to have root access to install unrar.

try this with the sudo command, enter password and it should install

sudo apt-get install unrar

---

