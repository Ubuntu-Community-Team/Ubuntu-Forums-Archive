---
title: "Strange problem with Xchat-gnome"
date: 2007-06-01
forum: General Help
---

### Post by NobleSavage on 2007-06-01
I'm using Feisty and I installed Xchat-gnome from Snaptic.  It worked perfect for a while.  Now when I launch it it shows up for a fraction of a second and then closes.  I can't get it to stay open.  I tried reinstalling, but that didn't work.  Any ideas?  I'm stuck on this one.

Thanks for any help.

---

### Post by Ambimom on 2007-06-01
Go to synaptic and install xchat irc client instead....

---

### Post by NobleSavage on 2007-06-01
Ok, just did that. It stays open for about 2 seconds and then vanishes. :(

---

### Post by rapolas on 2007-06-01
if it worked at first, and now stopped, so probably it's because of settings, you could try to remove .xchat folders from your home directory and then try to start it again. One more thing you can try to do is to start xchat from command line and see what errors you getting..:)

---

### Post by NobleSavage on 2007-06-01
noble@noble-laptop:~$ xchat
Segmentation fault (core dumped)


I'll try deleting the folders.

---

### Post by NobleSavage on 2007-06-01
Deleting the setting folders fixed the problem.  I wonder what went wrong?

---

### Post by Bluecircle on 2007-06-16
This fixed it for me too, thanks.

---

### Post by Manganic on 2007-07-08
Where exactly are these xchat folders?  I've looked everywhere, and even used the whereis command.  I've found the binary files, but can't seem to find the config files for xchat.

My problem started when I tried to configure xchat to connect to two different servers at the same time on startup (something it should be able to do.)  Since that point, I've been getting the segfault error.

Any help?

---

### Post by coarse.sand on 2007-07-10
The .xchat config folders are in your home directory, as someone said above. If you can't find them, enable "see hidden files", in Nautilus you can select the option under view or press control+h.

---

