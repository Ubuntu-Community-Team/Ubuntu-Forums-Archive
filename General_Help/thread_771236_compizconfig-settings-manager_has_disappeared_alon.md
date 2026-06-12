---
title: "compizconfig-settings-manager has disappeared along w/ my cube"
date: 2008-04-27
forum: General Help
---

### Post by |{urse on 2008-04-27
I havent done anything but update yesterday and the only 2 updates were compiz related, srry dint make note of the actual updates titles.

check this silliness out: 

> 
Unpacking compizconfig-settings-manager (from .../compizconfig-settings-manager_0.6.99~git20071005+3v1ubuntu0_i386.deb) ...
Setting up compizconfig-settings-manager (0.6.99~git20071005+3v1ubuntu0) ...
kurse@kurse-desktop:~$ compizconfig-settings-manager
bash: compizconfig-settings-manager: command not found
kurse@kurse-desktop:~$ 


---

### Post by Rocket2DMn on 2008-04-27
The correct command is
```
ccsm
```
You can also access from System->Preferences->Advanced Desktop Effects Settings

---

### Post by |{urse on 2008-04-28
thx for responding!

> kurse@kurse-desktop:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'


any ideas on initializing compizconfig.Plugin?

---

### Post by Rocket2DMn on 2008-04-28
> **|{urse said:**
> thx for responding!

any ideas on initializing compizconfig.Plugin?

Is compiz running OK right now?  I'm not entirely sure what compizconfig.Plugin is, but maybe you can find something for it under ccsm.

---

### Post by |{urse on 2008-04-28
just fixed this! 

[https://bugs.launchpad.net/compizconfig-settings-manager/+bug/143962]("https://bugs.launchpad.net/compizconfig-settings-manager/+bug/143962")

removed compizconfig-settings-manager python-compizconfig

installed compizconfig-settings-manager (0.5.2+git20070912-0ubuntu1)
          python-compizconfig (0.5.2+git20070912-0ubuntu1)

as per goldencut's post

thx, i hope this helps someone else too.

---

### Post by |{urse on 2008-04-28
no it wasnt running at all after an update via synaptic. really weird, the icon in the menu disappeared but the entry was still there and there was no compositing windowmanager running :confused: it's all good now tho

---

