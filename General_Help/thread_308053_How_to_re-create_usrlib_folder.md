---
title: "How to re-create /usr/lib folder"
date: 2006-11-27
forum: General Help
---

### Post by hfgfdhrtjtyjtykjtjd on 2006-11-27
I accidentally deleted my /usr/lib folder with the command
sudo rm /usr/lib/* 

(admittet -  it was a rather stupid mistake)

This caused problems, of course, especially with the graphic user-interface, but i managed to correct them by installing a fresh Ubuntu on another partition and copy the /usr/lib directory from this install back to the original. However - some programs are now refusing to start, even though i uninstall them and re-install them from synaptic package manager.

Are there anyone who can suggest a clever solution to this, or do I have to backup all my data and start from a fresh install?

Thanks in advance
Lasse Folkersen 

--------------

He for whom all appropriate username variations was taken.

---

### Post by aysiu on 2006-11-27
Considering the installation took me about twenty minutes, I'd say a backup and fresh install is your best bet, especially since copying the /usr/lib folder from another installation didn't work.

You may want to also [create a separate /home partition](http://www.psychocats.net/ubuntu/separatehome).

---

### Post by scrooge_74 on 2006-11-27
maybe from synaptic you could install libraries, but i think it would be easier to move your /home folder to another drive and reinstall

---

### Post by hfgfdhrtjtyjtykjtjd on 2006-11-28
Ok thx a lot

I'll do that

---

