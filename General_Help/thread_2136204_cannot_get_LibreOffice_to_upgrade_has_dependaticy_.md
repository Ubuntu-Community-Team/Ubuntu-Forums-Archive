---
title: "cannot get LibreOffice to upgrade: has dependaticy problem"
date: 2013-04-16
forum: General Help
---

### Post by jlh68 on 2013-04-16
Tried to repair broken apt.  LibreOffice. I get the following message:

> Setting up libreoffice-calc (1:4.0.2~rc2-0ubuntu1~precise1) ...
Setting up libreoffice-draw (1:4.0.2~rc2-0ubuntu1~precise1) ...
Setting up libreoffice-impress (1:4.0.2~rc2-0ubuntu1~precise1) ...
Setting up libreoffice-gtk (1:4.0.2~rc2-0ubuntu1~precise1) ...
Setting up libreoffice-gnome (1:4.0.2~rc2-0ubuntu1~precise1) ...
Setting up python-uno (1:4.0.2~rc2-0ubuntu1~precise1) ...
Setting up libreoffice-math (1:4.0.2~rc2-0ubuntu1~precise1) ...
Setting up libreoffice-writer (1:4.0.2~rc2-0ubuntu1~precise1) ...
Setting up libreoffice (1:4.0.2~rc2-0ubuntu1~precise1) ...
[COLOR="#FF0000"]Errors were encountered while processing:
 libreoffice-emailmerge[/COLOR][COLOR="#FF0000"][/COLOR]
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  [COLOR="#FF0000"]Trying to recover:
dpkg: dependency problems prevent configuration of libreoffice-emailmerge:[/COLOR]
 libreoffice-common (1:4.0.2~rc2-0ubuntu1~precise1) breaks libreoffice-emailmerge (<< 1:4.0.2~rc2) and is installed.
  Version of libreoffice-emailmerge to be configured is 1:4.0.2~rc1-0ubuntu1~precise2.
dpkg: error processing libreoffice-emailmerge (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libreoffice-emailmerge

The libreoffice-emailmerge is the dependent part that is incompatable with the rest of LibreOffice.
How do I repair it.  I have tried Synaptic Package Manager and the Ubuntu Software Center, and neither have worked yet.

---

### Post by ibjsb4 on 2013-04-16
nope, I was mistaken, edit out

---

### Post by gifford on 2013-04-17
Had the same problem and this is what I did. sudo apt-get purge libreoffice*, then sudo add-apt-repository ppa: libreoffice/ppa , then sudo apt-get update, then sudo apt-get install libreoffice. The ppa is for libreoffice 4.0.2 and will include future updates.

---

### Post by jlh68 on 2013-04-17
I am using LO 4.02.2.  I just uninstalled *libreoffice-emailmerge* and everythins is OK.  I probably don't have mailmerge but I don't use it anyway and I expect the next version of LO will correct the problem.

---

