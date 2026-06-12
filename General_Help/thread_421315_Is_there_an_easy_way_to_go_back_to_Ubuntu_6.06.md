---
title: "Is there an easy way to go back to Ubuntu 6.06?"
date: 2007-04-24
forum: General Help
---

### Post by clapper on 2007-04-24
I recently updated to 7.04, but I'm having early adapter problems. I'd like to go back to 6.06. Is there an easy way to do it? Can I just re-install? or must it be a clean install? Any help would be appreciated.

---

### Post by MetalMusicAddict on 2007-04-24
A clean install of either Dapper or Feisty would be best. Id go with Feisty. ;)

---

### Post by zvacet on 2007-04-24
What kind of problems do you have?You can allways install Dapper again,and of course be carefull not to lose your data or whatever you want to keep.If you have separate home parititon you are safe and if you don´t have one,make it.

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by pmdkh on 2007-04-24
I'm still pretty new, so someone correct me if I'm wrong, but you should be able to simply reformat your root partition using GParted.  When you insert the Live CD, you click on the icon to install.  That takes you into the installation process.  When you get to the appropriate screen, you select "Manually edit partition tables."  Then you'll select to reformat your root partition.  (Note: If you don't have this already, it helps to have a separate "/home" partition to save all of your personal files on.)  GParted will then install 6.06 where 7.04 was and that should be it.

Remember that it's always a good idea to back up your files.  Also, I'd recommend making a separate "/home" partition when you intsall 6.06 again if you don't already have one.

Does this answer your question?

---

