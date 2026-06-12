---
title: "[SOLVED] passwording trash"
date: 2008-04-26
forum: General Help
---

### Post by Zeotronic on 2008-04-26
Perhaps there are categories better suited to this question, but I wasn't sure... so when in doubt...

I want to put a password on deleting files in my trash... preferably the same password that is used in everything else in my system (I'm referring, of course, to my account password). Is there any way to do this? I bothered including my variant in the prefix because it probably matters.

---

### Post by SOULRiDER on 2008-04-26
Other users should not be able to delete your trash since it sin your home folder and they dont have write permissions there.

---

### Post by mali2297 on 2008-04-26
Your trashed files are located in the directory **~/.local/share/Trash/files/** which only you (and the superuser) can open.

---

### Post by Zeotronic on 2008-04-27
I know these things, but under statements such as those, it doesn't make sense why you must enter passwords all throughout operation (Synaptic, Network Manager, etc), no, I want a password on my trash in case someone happens upon my computer running, or I trust someone in my computer, and they get the inclination to delete my files. Both of which are possible because I have a little brother who hates me, and I am far too stupid to deny him use of my computer purely on those grounds.

---

### Post by mali2297 on 2008-04-27
An idea would be to change the ownership of the Trash directory to root. The problem is that you want to be able to move things to the Trash as a normal user, but not remove.

The solution I suggest is to change the file attribute to *append mode*:
```

sudo chattr +a ~/.local/share/Trash/files

```
This will allow you to add files to Trash but not empty it. If you want to be able to empty the trash, you need to remove the attribute:
```

sudo chattr -a ~/.local/share/Trash/files

```
You can make these commands into custom actions if you want. In that case, replace sudo with gksudo.

---

