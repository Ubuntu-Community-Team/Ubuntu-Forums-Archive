---
title: "[SOLVED] Can't Delete File"
date: 2008-01-14
forum: General Help
---

### Post by dethredic on 2008-01-14
There is a folder in my Trash called curl-7.17.1.

inside that is a docs folder, then an examples folder, and in that is a hidden .libs folder.

There are a lot of files with name relating to the internet.

I can't delete it because I don't have permission it says.

I assume I need to do something like cd trash, sudo delete files, but I am not sure what command(s) will work.



EDIT: this worked: rm -rf ~/.Trash/* for some reason it didn't work when I was root.

---

### Post by rodo-&gt;dave on 2008-01-14
yes, you are correct. You should cd ~/.Trash and then rm -rf curl-7.17.1

**the rm -rf will remove the curl-7.17.1 directory and everything underneath it.**

you might have to sudo rm -rf curl-7.17.1 to get them deleted.

---

