---
title: "FireFox and flash"
date: 2005-09-23
forum: General Help
---

### Post by ngms27 on 2005-09-23
Hi,

For some reason I cannot get Firefox with flash working correctly for this site:

[http://www.capitalspreads.com](http://www.capitalspreads.com)

essentially I see no live prices on the flash panel.

I have upgraded to Firefox 1.07, I have uninstalled and reinstalled Flash with a fresh download.

This works fine on a machine using the same combination on Vector Linux (hey its a P11 450 and Vector works well on it)

Any ideas?

---

### Post by aysiu on 2005-09-23
Have you tried this? ```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

---

### Post by ngms27 on 2005-09-23
Yes, I get:

ngms27@ubuntu:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree

JonnyT

---

### Post by Hairy_Palms on 2005-09-23
u must add the universe and multiverse repositiories in synaptic, or you wont find flash and some other things

---

### Post by az on 2005-09-23
You need to install gsfonts-x11 for flash to be able to show fonts properly.

[http://packages.ubuntu.com/hoary/x11/gsfonts-x11](http://packages.ubuntu.com/hoary/x11/gsfonts-x11)

The message is displayed when you install the flashplayer-plugin package.

apt-get install gsfonts-x11 
or just use synaptic to install the package.

---

### Post by aysiu on 2005-09-23
[QUOTE=Hairy_Palms]u must add the universe and multiverse repositiories in synaptic, or you wont find flash and some other things[/QUOTE] To do so, follow these instructions:

[http://www.frankandjacq.com/ubuntuguide/5.04/#extrarepositories](http://www.frankandjacq.com/ubuntuguide/5.04/#extrarepositories)

If you're using Breezy (5.10), then replace all the *hoary* references with *breezy*.

---

### Post by ngms27 on 2005-09-23
Thank you very much!!!

Installing the fonts did the trick.

I think I'm missing a few things here by manually installing and not using the repositories!

JonnyT

---

### Post by az on 2005-09-23
From a command line type

sudo apt-get -f install 

to resolve any dependancies you need.

---

### Post by az on 2005-09-23
[QUOTE=ngms27]

I think I'm missing a few things here by manually installing and not using the repositories!

JonnyT[/QUOTE]


If all you installed was that gsfonts-x11 package, you should not be missing anything else.

I will ask on #ubuntu-motu if the depends for both packages (flashplugin-nonfree and flashplayer-mozilla) can be changed to depend on gsfonts-x11.  Flashplayer-mozilla does not mention it in the dsc, and flashplugin-nonfree only has it as a recommends.

---

