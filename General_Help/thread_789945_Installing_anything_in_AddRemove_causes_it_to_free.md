---
title: "Installing anything in Add/Remove causes it to freeze."
date: 2008-05-11
forum: General Help
---

### Post by theytookpenny on 2008-05-11
I recently just tried to install most of the gstreamer packages and exaile music player and uninstall rhythmbox. But when it was installing, it was taking ages for rhythmbox to unistall, so I ctrl+c to cancel. I went back to try to install the above packages without uninstalling but it wouldn't work. So I did sudo apt-get clean and tried once more, but again it failed. I continued this with some other packages and even restarted it and tried again. So far I can conclude that it happens to all packages and that there's definitely something wrong with add/remove. Can someone please help me?

EDIT:
I tried to download some updates, but I clicked on the notification I icon, after the window loaded I got this message:

> Not all updates can be installed

Run a partial upgrade to install as many updates as possible

This can be caused by:
a previous update which didn't complete
problems with some of the installed software
unofficial software packages not provided by ubuntu
normal changes of a pre-release version of ubuntu


EDIT #2:
Fixed by running partial upgrade.

---

