---
title: "To uninstall LimeWire, do I just delete all of the files it put in my home directory?"
date: 2007-03-03
forum: General Help
---

### Post by rainwalker on 2007-03-03
I've decided to switch to FrostWire, and I'm not sure how I delete LimeWire off of my computer. Because it installed with a shell script, I can't remove it as a package (like with Synaptic) and I was wondering if I could just delete the "Incomplete", "LimeWire" and ".limewire" folders. Will that work?

---

### Post by taurus on 2007-03-03
This command will tell you where it has been installed to so you can remove it completely off your machine if you wish.

```
locate limewire
```

---

### Post by rainwalker on 2007-03-03
It gives me a REALLY long list, mostly image files and theme files, but it all seems to be in my ".limewire" directory. There's also stuff in my "LimeWire" directory (the "locate" was case-senstitive), so I'm guessing I should remove that too?

Also, I still have a ".frostwire" directory in my home folder, even though I completely removed the package with Synaptic. Is that normal?

---

### Post by taurus on 2007-03-03
> **rainwalker said:**
> It gives me a REALLY long list, mostly image files and theme files, but it all seems to be in my ".limewire" directory. There's also stuff in my "LimeWire" directory (the "locate" was case-senstitive), so I'm guessing I should remove that too?

Yes, you just have to remove them by hand then.

> Also, I still have a ".frostwire" directory in my home folder, even though I completely removed the package with Synaptic. Is that normal?

Yes, it is.  It will be there until you remove it by hand since all your configs are in ~/.frostwire.

---

### Post by Dylnuge on 2007-03-03
> **taurus said:**
> Yes, it is.  It will be there until you remove it by hand since all your configs are in ~/.frostwire.

Actually, you can remove your configuration files by using "Completely Remove Selected Package."

---

### Post by rainwalker on 2007-03-03
> **Dylnuge said:**
> Actually, you can remove your configuration files by using "Completely Remove Selected Package."

I did that, which is why I'm wondering if it's normal.
Does FrostWire work with Edgy and Beryl? "java -version" tells me I have version 1.6.0 installed, which will work, right?

---

### Post by Dylnuge on 2007-03-03
It may be that the directory is kept, but the files are deleated. People do stupid things-like install software in a system directory-which means programs usually don't remove directories.

Try "ls ~/.frostwire" and see if there are any files in it.

---

### Post by rainwalker on 2007-03-03
I get "bugs.data, frostwire.props, pub1.key, questions.props, tables.props, createtimes.cache, gnutella.net, pub2.key, responses.cache, themes, fileurns.bak, installation.props, pub3.key, simpp.xml, xml, fileurns.cache, library.dat, pub4.key", and "spam.dat"

---

### Post by Dylnuge on 2007-03-03
I would not worry about it.

---

### Post by rainwalker on 2007-03-04
Okay, thank you for all the help!

---

### Post by MichaelSM on 2007-03-10
Relating to this thread, I posted the following a couple of days ago:

Hello. Recently installed 6.10, and made a mistake trying to run LimeWire probably because of incorrect Java.(1.4.2) . The main problem is now when I try to do [I]ANYTHING[I] in Terminal it just gets to this point and stops:

michael@michael-desktop:~$ sudo apt-get install win32 codecs
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package limewire-free needs to be reinstalled, but I can't find an archive for it.
michael@michael-desktop:~$

In other words, I don't know what to do at this stage. I'd rather just chuck out LimeWire altogether, 'though to complicate things further one version seems to have been installed as accessible only by root.

Any help greatly appreciated. Nice forum Cheers, Michael.

---

### Post by rainwalker on 2007-03-10
I chucked LimeWire and installede FrostWire: [http://www.ubuntuforums.org/showthread.php?t=305337](http://www.ubuntuforums.org/showthread.php?t=305337)

---

### Post by MichaelSM on 2007-03-23
Perfect solution! Thank you. Mike.

---

