---
title: "can't pin chrome in dockbarx"
date: 2014-03-09
forum: General Help
---

### Post by george_s2 on 2014-03-09
Recently I tried out dockbarx and I noticed that when i tried to right click chrome in the panel to pin it to dockbarx the option to pin wasn't there.  I also tried dragging it to the panel but I got nothing.  
Pinning worked for all the other apps I tried so I don't know why it wouldn't work for chrome.  Can someone please tell me how to fix it cos i cant seem to find anything online that works
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 I just decided to run dockx through the terminal to see if it could tell me anything about why chrome cant be pinned.  I dragged the chrome shortcut from my desktop to dockx and this is what came up in the terminal

(dockx:5948): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE


(dockx:5948): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE
DockbarX reload
<class 'Xlib.protocol.request.QueryExtension'>


(dockx:5948): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE


(dockx:5948): Wnck-WARNING **: Unhandled action type _OB_WM_ACTION_UNDECORATE
ERROR: Couldn't read dropped file. Was it a desktop entry?
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dockbarx/dockbar.py", line 811, in launcher_dropped
    desktop_entry = DesktopEntry(path)
  File "/usr/lib/pymodules/python2.7/dockbarx/common.py", line 213, in __init__
    name = sg.get(n % lo) or sg.get(n % lo[:2])
TypeError: 'NoneType' object has no attribute '__getitem__'

---

### Post by Frogs Hair on 2014-03-09
I have pinned Chrome in dockbarx using the xfce session on more than one installation so it's possible but don't know what is causing the problem.

---

