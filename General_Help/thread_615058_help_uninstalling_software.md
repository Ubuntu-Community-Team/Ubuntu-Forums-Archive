---
title: "help uninstalling software"
date: 2007-11-16
forum: General Help
---

### Post by kasperfish on 2007-11-16
hi there,

i have problems with uninstalling software on my ubuntu system. especially with software that does not show up as installed in add/remove and synaptic.

there are a few scripts i compiled but they slow down the system (vmware player, screenlets,..). as i said these do not show up in synatic nor add/remove.

secondly i have a question on how obtain the best performance of your system: clean up unused files, broken software, ... does there exist tools for?

thanks guy's or girls!!

kasperfish

---

### Post by knutschr on 2007-11-16
To remove unused files:
```

sudo apt-get autoremove

```

I followed this even if I have a 3.2 MHz dualboot processor with 1 Gb RAM:
[http://ubuntuforums.org/showthread.php?t=107856&highlight=boost](http://ubuntuforums.org/showthread.php?t=107856&highlight=boost)
It sure works!

If you can't see your programs to delete them, start Adept or Synaptic from the system menu, and try again.

I think, though, that if you are experiensing low performance, it is something else causing it.

Coul you explain better?
'

---

### Post by kasperfish on 2007-11-16
thanks for the respons!!

after installing sreenlets my sytem slowed down. especially during booting. when i use the screenlets with compiz i've got bugs from the widgets (black widget screen). i think there occurred an error during compiling screenlets.

anyway the software does not show up in synaptic because i did not "checkinstalled" it. i just "make installed" it.

grtz kasper

---

### Post by knutschr on 2007-11-16
Can you rightclick the applet?
(I get the option to remove it)

If you get the name somehow:
```

sudo apt-get remove [name]

```

I am using Kubuntu.
I don't need the fancy things in Compiz Fusion that often make problems like this.

I recommand to remove it, time being :-)

---

