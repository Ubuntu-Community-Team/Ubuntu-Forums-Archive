---
title: "Removing software with synaptic"
date: 2008-06-15
forum: General Help
---

### Post by Bastaard on 2008-06-15
When I install a piece of software with the synaptic package manager, most of the time it grabs around 5-10 other software packages to install as they are dependencies. Lots of times however I install software and uninstall it a couple of minutes later when I find out it's not what I want.

When I try to uninstall the software with synaptic, it only grabs the main software package and all the other dependency bogus is just left on my hard drive. Thus my question: how can I remove all of the packages I just installed?

---

### Post by forestpixie on 2008-06-15
Use the Mark for Complete Removal - if there any residuals left you can get them on the status page - it won't however get rid of the config files hiodden in your home folder.

---

### Post by Pjotr123 on 2008-06-15
> **Bastaard said:**
> When I install a piece of software with the synaptic package manager, most of the time it grabs around 5-10 other software packages to install as they are dependencies. Lots of times however I install software and uninstall it a couple of minutes later when I find out it's not what I want.

When I try to uninstall the software with synaptic, it only grabs the main software package and all the other dependency bogus is just left on my hard drive. Thus my question: how can I remove all of the packages I just installed?

Choose "Complete removal" in Synaptic. That should remove all dependencies, provided that they aren't used by other apps as well.

Moet lukken zo!  :-)

---

### Post by Arlanthir on 2008-06-15
_If you just want to use Synaptic and avoid the command line, you can safely ignore my post, as they're just hints on how to clean the system using the terminal._

You can also (from time to time) check that no leftovers still remain by typing in a terminal:

```
sudo apt-get autoremove
```

The above command will remove from your system all the packages that were installed as dependencies and are not required anymore.
(be careful with any programs you might have installed without synaptic that may require these packages)

I think you might also be interested in the following:

```
sudo apt-get clean
```

This will clean your archive cache (the downloaded .debs)

or 

```
sudo apt-get autoclean
```

Same thing, but only for old packages.

---

### Post by Bastaard on 2008-06-15
In my experience, "complete removal" doesn't remove installed dependencies.

Thanks for the advice Arlanthir! I just did the autoremove option and it deleted some old files, which I know were dependencies of software I had installed and uninstalled recently. Cheers!

---

### Post by Arlanthir on 2008-06-15
Glad I helped =)

Don't forget to add [SOLVED] to the title if you have no further problems ;)

---

### Post by lolobu on 2008-06-15
Indeed, *complete removal* in Synaptic doesn't remove unused dependancies at all. The difference with simple removal is that it will remove the program **and** the configuration files for that program as opposed to just remove the program.
Unused dependies are called orphan packet and can be remove like that:
[LIST]
Install from Synaptic the packet *deborphan*
[/LIST]
[LIST]
In Synaptic : Configuration -> Filter
[/LIST]
[LIST]
Give a name to your filter like "Remove Orphans" and just select the option **orphan**
[/LIST]
[LIST]
Your new filter appears in the right column of Synaptic, just click on it. You will get a list of unused packet without any dependancy
[/LIST]

---

### Post by oldos2er on 2008-06-15
> **Bastaard said:**
> In my experience, "complete removal" doesn't remove installed dependencies.


 Complete removal in Synaptic means the package's config files in ~/ will be removed.

 I prefer to use aptitude in the terminal. It handles removal of unneeded dependencies better than apt-get.

---

