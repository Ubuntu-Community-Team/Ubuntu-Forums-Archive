---
title: "How do in dkpg -i a directory?"
date: 2005-10-24
forum: General Help
---

### Post by csscll on 2005-10-24
I'm installing some more software on a machine that's not connected to the net. Can I install them all, the packages of the software and their dependencies, with just one command or do I have to do an individual install for each package? 

Could I not do something like 

dpkg -i ./*.deb 

Can I do that? Thanks.

---

### Post by markr on 2005-10-24
I'm sure you can CD into the directory and issue

sudo dpkg -i *.deb.

You might need to be fast if you have lots of dependency problems as they may scroll off the screen.

Mark.

---

### Post by Xian on 2005-10-24
Just always put them all in your /home/username directory and issue the command that was posted by markr. That way you don't even have to cd to another location. You only need to issue a single command each time.

---

