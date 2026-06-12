---
title: "Dolphin in Lubuntu"
date: 2014-12-27
forum: General Help
---

### Post by Tim036 on 2014-12-27
I wanted to install dolphin (text editor)
How do you go about that.
xterminal stopped me and add programs only looked in what already existed.

very much a newbie here...

Any thoughts anyone ?

Tim

---

### Post by oldos2er on 2014-12-27
The only "dolphin" package I see in the repositories is the KDE-centric file manager. It looks like the dolphin text editor you're referring to is a Windows program; Windows programs do not run natively on Linux, but it may be possible to run it with Wine, but there are so many native text editors available, why not try one of them?

---

### Post by Tim036 on 2014-12-28
My mistake, Kate is my prefered text editor, Dolphin is like Files but has different  (better in some tasks than Files).

So how do I download them using Lubuntu ?

Many thanks for replying.

:  )))

Tim

---

### Post by oldos2er on 2014-12-28
I don't remember if Lubuntu has Synaptic Package Manager installed by default, but you can use lxterminal to install it (and any other packages you may want): ```
sudo apt-get update && sudo apt-get install kate dolphin synaptic
``` 

 [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

You may see references to Software Center in the above links, which is not installed in Lubuntu, but can be if you want it (just like Synaptic). All these programs, Synaptic, Software Center, and apt-get are front-ends to the APT packaging system Ubuntu uses. Allow yourself some time to find whichever one best fits your needs and preferences.

---

### Post by vasa1 on 2014-12-28
> **oldos2er said:**
> I don't remember if Lubuntu has Synaptic Package Manager installed by default, ...
It's included by default in Trusty: [http://packages.ubuntu.com/trusty/lubuntu-desktop](http://packages.ubuntu.com/trusty/lubuntu-desktop)

---

### Post by Tim036 on 2014-12-28
Many thanks Ann, I think that has fixed everything !

:  )))

Tim

---

### Post by Tim036 on 2014-12-28
Many thanks Ann, I think that has fixed everything !

:  )))

Tim

---

### Post by oldos2er on 2014-12-28
Welcome. Enjoy Lubuntu.

@vasa1 Thanks, now I know.  :)

---

