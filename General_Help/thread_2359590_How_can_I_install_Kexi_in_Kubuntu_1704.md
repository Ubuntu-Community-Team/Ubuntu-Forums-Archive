---
title: "How can I install Kexi in Kubuntu 1704?"
date: 2017-04-25
forum: General Help
---

### Post by zerubbabel on 2017-04-25
I just installed Kubuntu 17.04 in a virtual box in order to try out Kexi, but after installing the Calligra Suite there is still no Kexi, but only their word processing and spreadsheet applications. How can I install their Kexi database application?

---

### Post by ajgreeny on 2017-04-25
I thought kexi was a dependency of calligra; it certainly is in 16.04 so I am surprised if it is not also the case in 17.04.

Try starting kexi in terminal to see if it is simply the kexi.desktop file (launcher) that is missing for some reason.

---

### Post by zerubbabel on 2017-04-26
Nope, can't run it from the commandline either.

---

### Post by howefield on 2017-04-26
Looks like kexi dropped as a Calligra dependency after 16.10 for some reason.

[http://packages.ubuntu.com/yakkety-updates/calligra](http://packages.ubuntu.com/yakkety-updates/calligra)
[http://packages.ubuntu.com/zesty/calligra](http://packages.ubuntu.com/zesty/calligra)

It is not available in the Ubuntu repositories as far as I can tell, you might need to look for a ppa, snap or other universal package format or compile from source.

---

### Post by zerubbabel on 2017-04-26
I gave up on running Kubuntu in a virtual box and just installed Kexi in my Mint Mate environment via the kubuntu ppa. I had hoped to avoid cluttering up my Mint installation with all the Kubuntu dependencies just to try out Kexi. It installed fine, but unfortunately the version in that ppa is versioin 2.9.7, not 3.0.1.

---

