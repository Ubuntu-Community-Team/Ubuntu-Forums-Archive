---
title: "doesnot launch!"
date: 2008-06-18
forum: General Help
---

### Post by ravicplk on 2008-06-18
i successfully installed compizconfig settings manager. It appears in 
system>preferences
but the thing is when i click on that,it does not launch, nothing happens.
what seems to be the problem??

my ubuntu version is 7.10 gusty gibbon

thanks in advance

---

### Post by rune0077 on 2008-06-18
Open a terminal and launch it from there:

```
ccsm
```

Paste the error-output here.

---

### Post by ravicplk on 2008-06-18
> **rune0077 said:**
> Open a terminal and launch it from there:

```
ccsm
```

Paste the error-output here.

ravicplk@ravicplk-desktop:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

this is the error

---

### Post by rune0077 on 2008-06-18
It seems you got a bad file there. Have you tried just reinstalling ccsm?

---

### Post by ravicplk on 2008-06-18
> **rune0077 said:**
> It seems you got a bad file there. Have you tried just reinstalling ccsm?

yep i did several times

---

### Post by rune0077 on 2008-06-18
That's strange. Did you install it from Synaptic?

Also, do you have Compiz running? (can you enabled the advanced effects in System > Preferences > Appearance?)

EDIT: also make sure you have Python2.5 installed

---

### Post by ravicplk on 2008-06-18
> **rune0077 said:**
> That's strange. Did you install it from Synaptic?

Also, do you have Compiz running? (can you enabled the advanced effects in System > Preferences > Appearance?)

yes..

and in the appearence>visual effects .. can enable extra effects. and there is custom effect option. but custom effect preferences also does not launch

---

### Post by Happy_Man on 2008-06-18
> **ravicplk said:**
> yes..

and in the appearence>visual effects .. can enable extra effects. and there is custom effect option. but custom effect preferences also does not launch
Well, that's only logical, seeing as ccsm and the custom preferences are one and the same. :p

Do you have the correct version of python installed? Did you try purging the computer of ccsm and then trying to reinstall?

```
sudo apt-get purge ccsm
sudo apt-get install ccsm
```

---

### Post by ravicplk on 2008-06-18
> **Happy_Man said:**
> Well, that's only logical, seeing as ccsm and the custom preferences are one and the same. :p

Do you have the correct version of python installed? Did you try purging the computer of ccsm and then trying to reinstall?

```
sudo apt-get purge ccsm
sudo apt-get install ccsm
```

oops sorry sorry .i am really new to this ubuntu thing,,

an error message came when purging

ravicplk@ravicplk-desktop:~$ sudo apt-get purge ccsm
[sudo] password for ravicplk:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ccsm

---

### Post by ravicplk on 2008-06-18
python 2.5 is installed

---

### Post by Happy_Man on 2008-06-18
Ah, so then it's not installed. Go ahead and use ```
sudo apt-get install compizconfig-settings-manager
``` to install it.

---

### Post by rune0077 on 2008-06-18
Replace ccsm with compizconfig-setting-manager. That's what Synpatic calls it.

---

### Post by ravicplk on 2008-06-18
> **Happy_Man said:**
> Ah, so then it's not installed. Go ahead and use ```
sudo apt-get install compizconfig-settings-manager
``` to install it.

:confused::confused::confused::confused:
ravicplk@ravicplk-desktop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for ravicplk:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 214 not upgraded.

---

### Post by Happy_Man on 2008-06-19
Hmmm... when was the last time you updated? (I only ask because of the line "0 upgraded, 0 newly installed, 0 to remove and **214** not upgraded). There may be an update in there that solves this. 

Also, try deleting the ~/.config/compiz/compizconfig folder. That's a reset of every user setting, which may solve the issue.

---

