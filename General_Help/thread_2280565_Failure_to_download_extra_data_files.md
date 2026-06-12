---
title: "Failure to download extra data files"
date: 2015-05-31
forum: General Help
---

### Post by Alduins_Khajiit on 2015-05-31
EVERY TIME my computer tries to update, I ALWAYS get the following message

[B]Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

flashplugin-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.[/B]

and NO MATTER HOW MANY TIMES I click "run this action", the console comes up to install it and asks for my password again but ALWAYS gives the SAME message AGAIN!
 EVERY TIME!!

Please help me fix

---

### Post by Bashing-om on 2015-05-31
Alduins_Khajiit; Hello;

Maybe, try and see what results ?
```

sudo apt-get purge flashplugin-installer
sudo apt-get install flashplugin-installer

```
If it does not (re-)install, we get some additional info to work with.
Post the errors - between code tags - 
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

