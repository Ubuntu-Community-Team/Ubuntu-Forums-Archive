---
title: "Multiple versions of wine at the same time?"
date: 2007-02-01
forum: General Help
---

### Post by tictacman on 2007-02-01
I've begun to use wine for the first time try and wean myself of using  my windows partition.  I followed the miss marple's guide to  install ripit4me using 
wine_0.9.5-winehq-1_i386.deb and it works fantastic.

But ripit4me is not the only windows application i want to use.  There are other applications I would also like to use but the guides I'm looking at suggest a different version of wine.  So what do I need to do and how do others get by? 

 Can I have more than one wine package installed?  Or is it a case of uninstall reinstall to different version and backup different .wine directories for different jobs which seems like a bit of a hassle.

---

### Post by pseudonym on 2007-02-01
You can only one run .deb packaged version of wine at a time. Another version running on the same system would need to be compiled from source and configured to install into a different directory, like [this example]("http://wiki.jswindle.com/index.php/Installing_Wine#Multiple_Installs") from the [wine wiki]("http://wiki.jswindle.com/index.php/Main_Page"). But I doubt you'd want to be doing that.

Your best bet is to go with the current version from [winehq]("http://www.winehq.org/site/download-deb"). Because some instructions specify one version of wine, doesn't mean the program will only work with that version. You can always set different defaults for different applications using the winecfg setup utility if need be. Tips on doing this are in the documentation section of winehq and also the wine wiki.

Other (non-free) options are [Cedega]("http://www.transgaming.com/index.php?module=ContentExpress&func=display&ceid=2&meid=-1") for games and [Crossover Office]("http://www.codeweavers.com/") for other windows applications.

---

### Post by tictacman on 2007-02-01
Ok thanks for the post. Your right about compiling it from source, I don't think its a viable solution.  I have noticed that for some reason not every thing runs on the newest install of wine. Some reasons older versions work better with certain apps.  I don't understand that, but hey, if it works then I'm happy :D 

I think I will backup the .wine directory and the specific version of wine it works with into individuals folders.  Seems like a pain, but it is unlikely I'm going to use the different apps at the same time, or for that matter any of them very often.  Just maxing out the functionality of using ubuntu.

Are there any other configuration files I need to be aware of when using different installs of wine or is it just the .wine folder?

---

### Post by pseudonym on 2007-02-01
> **tictacman said:**
> I have noticed that for some reason not every thing runs on the newest install of wine. Some reasons older versions work better with certain apps.  I don't understand that, but hey, if it works then I'm happy :D
Wine can be a strange beast. I think it can only be fully comprehended by those who've gathered up all the runes from across the universe :) Seriously, though, stuff like that is not uncommon - eg. something new added by the developers, which breaks something old. You'll often find the old app suddenly works again in a new version, though. Go figure???

> **tictacman said:**
> I think I will backup the .wine directory and the specific version of wine it works with into individuals folders.  Seems like a pain, but it is unlikely I'm going to use the different apps at the same time, or for that matter any of them very often.
You do not want to do this. Your ~/.wine directory will work no matter which version of wine you have installed, and your backed up wine versions will not work again by restoring them to their previous location. This can only be done by uninstalling/installing via Ubuntu's package management system. Copying those files/folders will not achieve anything.

> **tictacman said:**
> Are there any other configuration files I need to be aware of when using different installs of wine or is it just the .wine folder?
The ~/.wine folder is all you need. When you change wine versions you need to first uninstall the old one before installing the new one. Doing a simple upgrade is not advised.

Also, once the new version is installed, open up a terminal and type 'wineprefixcreate' (without quotes). This tells the 'fake registry' on your 'fake c drive' in your ~/.wine folder to recognise the new version of wine.

---

### Post by tictacman on 2007-02-01
Thanks for the post it was very informative.  Not being able to backup my wine settings is a bit disappointing.  I will just have to make a  backup of each windows install program, with the dlls and the wine version and the howto guide and stick in a folder then.  Shouldn't really take that long to set up again.  Just have to keep my fingers crossed for a version of wine that will do everything I need. We can dream :D

---

### Post by pseudonym on 2007-02-01
> **tictacman said:**
> Not being able to backup my wine settings is a bit disappointing.  I will just have to make a  backup of each windows install program, with the dlls and the wine version and the howto guide and stick in a folder then.
Just to clarify - you can back up your ~/.wine folder if you wish, but it is not tied to any particular version of wine, is what I meant to say. You can also keep temporarily non-working windows apps in this folder - it just means they won't work until you are running a version of wine where they do.

---

