---
title: "Apper Updates (of Flash) Routinely Break Flash (but report installed OK . . )"
date: 2013-04-10
forum: General Help
---

### Post by GregA on 2013-04-10
Some time after installing Kubuntu 12.04, I noticed that Flash is not being updated when Apper advises of bug fixes, etc.   I think one time of about 15 or so, the update process will succeed, but normally I have to go into Synaptic and mark Flash for "re-installation" - - then it works again on the sites that _require_ flash.

Here's a couple snapshots to illustrate - the first pic just shows a hanging update after doing a rescan for updates  - - in other words, package kit didn't succeed . . . , the second is the detail view after starting the re-install via Synaptic.  It seems the normal update process just doesn't succeed in downloading the new flash update from whatever source (I assume the updates are at Adobe's site . . or perhaps another directory on the Ubuntu servers reserved for proprietary apps??  Just speculating on this though.)

[[IMG]http://imageshack.us/scaled/medium/11/flashupdatefailures.jpg[/IMG]](http://imageshack.us/photo/my-images/11/flashupdatefailures.jpg/)

[[IMG]http://imageshack.us/scaled/medium/585/flashreinstallviasynapt.jpg[/IMG]](http://imageshack.us/photo/my-images/585/flashreinstallviasynapt.jpg/)

---

### Post by Aide9aic on 2013-04-21
FWIW, I've generally found the Flash plugin from the partner repository to be less troublesome. Enable the "Canonical Partners" repository in Software Sources. Then purge existing **flashplugin-*** packages. Next, install **adobe-flashplugin** and **adobe-flash-properties-kde**. That second package will create a module in System Settings that allows you to configure various Flash Player properties. It lands in the Lost and Found group, because the packaging is screwed up, but it works.

---

### Post by GregA on 2013-05-15
Hi Steve,

Just saw your suggestion earlier today, and I enabled the partners source.   So tonight's flash update went a whole bunch smoother.   Thanks!

---

