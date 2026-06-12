---
title: "AutoKey-gtk not working in Ubuntu 12.04"
date: 2012-10-26
forum: General Help
---

### Post by dragonfly41 on 2012-10-26
I can't get AutoKey-gtk (version                                 0.90.4-0~precise) to work in Ubuntu 12.04 .. it closes unexpectedly when launched and no icon appears in top tool bar.

I've found reference to a bug

[https://bugs.launchpad.net/ubuntu/+source/autokey/+bug/970581](https://bugs.launchpad.net/ubuntu/+source/autokey/+bug/970581)

> By default, AutoKey does not work with Ubuntu 12.04 because it is not  present in the Unity Panel whitelist. By default, the Unity panel  whitelist is set to ['JavaEmbeddedFrame', 'Wine', 'Update-notifier']. In  order for certain applications, such as Desura and AutoKey to work  properly, they need to be added to this whitelist, otherwise they will  not function properly at all.How can I get AutoKey-gtk to work?


[COLOR=DarkRed][Later edit]

On further reading 

[http://code.google.com/p/autokey/issues/detail?id=204](http://code.google.com/p/autokey/issues/detail?id=204)

I can launch from command line ..

**[COLOR=Navy]autokey-gtk -l[/COLOR]**

and there is a grayed out icon in top bar (no AutoKey icon) which allows me to launch into AutoKey window.

Why no icon?    I have the same grayed out effect with Ubuntu One launcher in top toolbar.

[/COLOR]

---

