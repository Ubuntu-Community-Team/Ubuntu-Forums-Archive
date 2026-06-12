---
title: "Strange behavior--Bridge Commander / Wine"
date: 2008-01-19
forum: General Help
---

### Post by Holonet on 2008-01-19
Ok I'm trying to run Star Trek:  Bridge Commander 1.1 under wine (latest version).  I installed the game, applied the 1.1 patch, then used a cracked .exe file because it doesn't properly detect the CD.

Weird thing here...  If I double-click the executable, I get a runtime error...but if I run stbc.exe from a terminal, the game runs.  I got this output at the end:

Exception TypeError: 'call of non-function (type None)' in <method TGPoint3.__del__ of TGPoint3 instance at 1467730> ignored
Exception TypeError: 'call of non-function (type None)' in <method TGPoint3.__del__ of TGPoint3 instance at 146771c> ignored
Exception TypeError: 'call of non-function (type None)' in <method TGPoint3.__del__ of TGPoint3 instance at 1467758> ignored
Exception TypeError: 'call of non-function (type None)' in <method TGPoint3.__del__ of TGPoint3 instance at 1467780> ignored
Exception TypeError: 'call of non-function (type None)' in <method TGPoint3.__del__ of TGPoint3 instance at 14677a8> ignored
Exception TypeError: 'call of non-function (type None)' in <method TGPoint3.__del__ of TGPoint3 instance at 14677e4> ignored
Exception TypeError: 'call of non-function (type None)' in <method TGPoint3.__del__ of TGPoint3 instance at 1467708> ignored
Exception TypeError: 'call of non-function (type None)' in <method TGPoint3.__del__ of TGPoint3 instance at 14677f8> ignored
Exception TypeError: 'call of non-function (type None)' in <method TGPoint3.__del__ of TGPoint3 instance at 14677d0> ignored
Exception TypeError: 'call of non-function (type None)' in <method TGPoint3.__del__ of TGPoint3 instance at 146776c> ignored
Exception TypeError: 'call of non-function (type None)' in <method TGPoint3.__del__ of TGPoint3 instance at 1467794> ignored
Exception TypeError: 'call of non-function (type None)' in <method TGPoint3.__del__ of TGPoint3 instance at 1467744> ignored
Exception TypeError: 'call of non-function (type None)' in <method TGPoint3.__del__ of TGPoint3 instance at 14677bc> ignored
fixme:d3d:IWineD3DDeviceImpl_Release (0x14aa68) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x116a940 with type 1,WINED3DRTYPE_SURFACE
fixme:d3d:dumpResources Leftover resource 0x127aa88 with type 1,WINED3DRTYPE_SURFACE
err:d3d:IWineD3DDeviceImpl_Release Context array not freed!

Anyone able to explain why it would work in one and not the other?

---

### Post by Holonet on 2008-01-21
Ok an update...to make it even weirder...I tried it again today...and for what reason I know not, now it won't work at all, I get a render error...bizarre.

---

