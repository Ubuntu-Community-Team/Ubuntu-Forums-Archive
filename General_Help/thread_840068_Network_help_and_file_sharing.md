---
title: "Network help and file sharing"
date: 2008-06-25
forum: General Help
---

### Post by nucklearknight on 2008-06-25
I am using a Live CD to boot into an old computer and I want to move some of the files to another computer. How would I do this over the network?

---

### Post by owlgorithm on 2008-06-25
LiveCD will let you install software using aptitude and Synaptic in live mode, but it would be better to use a terminal with commands like scp (secure copy) and sftp (secure FTP). From the old computer, type 

scp -rf files user@newcomputer:newdirectory

into the terminal. Use "man scp" to tweak the options.

There are many ways to do this, but this is the easiest -- the hardest part is getting the new computer's IP address (use ifconfig) and then making sure it allows scp (which we'll work on further if it doesn't).

---

### Post by nucklearknight on 2008-06-25
Could I move them to an external flash drive instead?

---

### Post by owlgorithm on 2008-06-25
Yes, you could also move them that way, and it is easier so long as you don't have a large volume of files to move -- doing it over and over drives me crazy, at least.

Use drag-and-drop in Nautilus (the built-in file browser) or the "cp -rf" command in the terminal. Use "man cp" in terminal to find out more about the different options.

---

