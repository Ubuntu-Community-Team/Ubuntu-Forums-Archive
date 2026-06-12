---
title: "Problems with steam and compiz fusion..."
date: 2008-04-10
forum: General Help
---

### Post by JockeG on 2008-04-10
Hi!!

I have some problems with my steam and compiz fusion.... To begin with steam it just exits when i'm tryin' to install some game on it, for example Counter-Strike. To error message i get in the terminal is:

err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set

 And the problem with compiz fusion is that i't won't start... When i'm tryin to star CCSM I get this error message:

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

 Do anyone now what the problem is??

// Jocke

---

