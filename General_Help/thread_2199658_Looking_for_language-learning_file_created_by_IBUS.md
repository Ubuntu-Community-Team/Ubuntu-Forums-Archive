---
title: "Looking for language-learning file created by IBUS"
date: 2014-01-15
forum: General Help
---

### Post by daygan on 2014-01-15
I use IBUS to type Chinese characters. The application is capable of learning frequently used phrases as the user interacts with it, so that when the user types, more frequently used phrases are offered for input choices before default characters. Recently, my system experienced a problem that caused the drive's remaining storage space to become critically low, resulting in the loss of some user settings in a few of the applications that were running at the time. My language input records were also lost, and years of system learning of commonly used phrases, proper names, and language habits have now been lost. I believe that there must be a file that stores these records somewhere that may have become locked or unusable, resulting in the creation of a new, blank records file. I would like to find this file and try to replace the new file with the old one if possible. Does anyone know where IBUS stores the language input file that keeps information such as frequently used phrases and words?

---

### Post by Bashing-om on 2014-01-15
daygan;

Have you now obtained the operating overhead the system requires ? 

On the issue of ibus files:
> 
sysop@1310mini:~$ sudo find / -name IBUS
[sudo] password for sysop: 
sysop@1310mini:~$ sudo find / -name ibus
/etc/apparmor.d/abstractions/ibus
sysop@1310mini:~$


What results are found from:
```

ls -la /etc/apparmor.d/abstractions/ibus

```
If the files are not there, maybe there will be some config files that will direct our attention to a place where they may be written.
Then again, my output:
> 
sysop@1310mini:~$ file /etc/apparmor.d/abstractions/ibus
/etc/apparmor.d/abstractions/ibus: [color=blue]ASCII text[/color]

Shows this file as a text file, might read it and see if there is any help there.

[INDENT][INDENT]hey, it's a thought
[/INDENT][/INDENT]

---

