---
title: "Uninstall Nautilus from 14.04"
date: 2014-06-03
forum: General Help
---

### Post by satish_j on 2014-06-03
I recently installed Trusty Tahr and was really very disappointed with the shipped-in Nautilus version.With every Dist upgrade,one or more useful feature of Nautilus is removed.This time,compact view feature is removed,which i used very frequently in earlier LTS releases.
Iam now done with Nautilus and would like to install Nemo File manager.(which,as i googled,has the compact view feature)
My question is:
1. How do i completely remove Nautilus?
2. I can find Nemo in software centre(of 14.04).Can i install it from there or need to install manually from source?

---

### Post by grumblebum2 on 2014-06-03
Nemo in the ubuntu repos is functional but for a more up to date version
use this guide.
[http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html](http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html)

It shows you how to set nemo as the default file manager.
Not really necessary to remove nautilus but if you must, use synaptic
as it will show you what else may be uninstalled.
```
sudo apt-get install synaptic
```
If I uninstall nautilus here it will also uninstall gnome-session-flashback.

---

### Post by slickymaster on 2014-06-03
> **satish_j said:**
> I recently installed Trusty Tahr and was really very disappointed with the shipped-in Nautilus version.With every Dist upgrade,one or more useful feature of Nautilus is removed.This time,compact view feature is removed,which i used very frequently in earlier LTS releases.
Iam now done with Nautilus and would like to install Nemo File manager.(which,as i googled,has the compact view feature)
My question is:
1. How do i completely remove Nautilus?
2. I can find Nemo in software centre(of 14.04).Can i install it from there or need to install manually from source?

Please be aware that Nautilus is so integrated in Ubuntu that you can't remove it without killing the desktop. Do the following```
sudo apt-get remove -s nautilus
```
to see exactly what would be removed. The "-s" means "No action; perform a simulation of events that would occur but do not actually change the system."

On the other hand, you don't need to remove Nautilus - just set Nemo as default - [see here how]("http://www.webupd8.org/2013/10/install-nemo-with-unity-patches-and.html").

---

### Post by LastDino on 2014-06-03
Do not remove Nuti, I've had occasions when I broke my system trying to do that. Simply install Nemo and set it to defualt as suggested above.

Usually, it is best practice to not remove default packages, espcially important ones like file manager. Eventhough, quite admitanly, Nuti is failing at both functionality (Which it had) and snappy/light (Which it aims) ends. 

I use nemo for only one reason over Nuti, it can do dual window with F3, which Nuti can't anymore :)

---

### Post by grumblebum2 on 2014-06-03
Is it really that hard to write "nautilus"?
It won't hurt to uninstall as long as you don't use the software center and take note what else is to be uninstalled.

---

### Post by LastDino on 2014-06-03
> **grumblebum2 said:**
> Is it really that hard to write "nautilus"?
It won't hurt to uninstall as long as you don't use the software center and take note what else is to be uninstalled.

Obviously, yes ;)

---

