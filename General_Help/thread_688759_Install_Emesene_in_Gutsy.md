---
title: "Install Emesene in Gutsy"
date: 2008-02-05
forum: General Help
---

### Post by jorgecarrillo150990 on 2008-02-05
Hello everyone.
I had a problem installing emesene in gutsy.
I followed all the steps that are in the tutorials, from editing the source.list, to the sudo apt-get install emesene. But something goes wrong.
It says that the .deb is obsolete and now I can't install emesene.
ANy other ways to install it?

---

### Post by ch_123 on 2008-02-16
Use subversion. First, run ```
sudo apt-get install subversion
```. 
Then type in "cd /home/[your username]" then run
```
svn co https://emesene.svn.sourceforge.net/svnroot/emesene/trunk/emesene emesene
```
Then you can create a shortcut to 
```
/home/[Your Name]/emesene/emesene
```
on your desktop or wherever you want.

---

