---
title: "Adobe Flash Plugin Update Inconsistencies - Solution?"
date: 2014-07-14
forum: General Help
---

### Post by Karlchen on 2014-07-14
Hello, folks.

[U]Preface:
[/U]I am using Ubuntu 12.04 64-bit Unity and Ubuntu 14.04 64-bit Unity. Yet, the issue is not limited to a particular Ubuntu version or to  a particular desktop environment.

_2 ways of getting the most recent Adobe Flash plugin for Firefox_
Basically there are 2 ways of getting the recent Adobe Flash plugin, current version 11.2.202.394, through the Ubuntu repositories:
Either you use the package flashplugin-installer or you use adobe-flashplugin plus adobe-flash-properties-gtk. (The latter is why I mentioned Unity.)

_Problem with flashplugin-installer:_
flashplugin-installer will download [adobe-flashplugin_11.2.202.394.orig.tar.gz]("http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.394.orig.tar.gz"), extract the flash plugin which corresponds to your architecture, 32-bit or 64-bit, and install it. It will, however, not install adobe-flash-properties-gtk, although it is present in the .tar.gz archive.
Reason?
Solution?

[U]Problem with adobe-flashplugin:
[/U]As a rule adobe-flashplugin and adobe-flash-properties-gtk will take a day or 2 longer to be updated than flashplugin-installer.
But this time, update from 11.2.202.378 to 11.2.202.394, this update does not seem to come at all.
"apt-get update" simply does not learn about the updated .deb packages. Synaptic confirms the latest adobe-flashplugin were 11.2.202.378.
This is extremely weird, because the updated .deb packages can be spotted in the same repository server folder where flashplugin-installer gets its adobe-flashplugin_11.2.202.394.orig.tar.gz: [http://archive.canonical.com/pool/partner/a/adobe-flashplugin](http://archive.canonical.com/pool/partner/a/adobe-flashplugin)
Reason?
Solution?

_Plight:_
flash-plugininstaller is faster to provide updates, but by using flashplugin-installer I will lose adobe-flash-properties-gtk, although it is present in the .tar.gz from which flashplugin-installer installs.
Clinging to adobe-flashplugin will preserve adobe-flash-properties-gtk, but the available updated  .deb packages are simply not delivered to me.
(All other updated software packages seem to be detected by "apt-get" properly and offered for upgrading. Just these 2 adobe packages are on the server, but not pushed out to the users for whichever reason.)

Can anybody confirm my observations?
Does anybody know why things are they way they are?
Any good suggestion how to workaround the plight?

Kind regards,
Karl

---

### Post by mvario on 2014-07-16
Yup, from my observations I can confirm your conclusions.  And I'm still waiting for 11.2.202.394.  The packages have been built and are sitting in Proposed, but aren't updating.  In this instance one might download the .deb's and install them manually.  I may try that.

---

### Post by Karlchen on 2014-07-19
Hello, mvario.

Thanks a lot for confirming my findings.
 And about your workaround of manually downloading the appropriate .deb files and installing them: this is what I did on a few systems.
(1) uninstalled the adobe-flash-properties-gtk
(2) updated the adobe-flashplugin (11.2.202.394)
(3) installed the adobe-flash-properties-gtk (11.2.202.394)

Hope someone can be bothered to move Adobe Flash Plugin 11.2.202.394 from *proposed* to *partner* soon, before the next Adobe patch day will arrive. ;)

Have a nice sunny weekend.
Karl

---

### Post by Karlchen on 2014-08-15
Just a final remark:
Now that Flash 11.2.202.400 has been released, everything seems to be back to normal. Could upgrade to adobe-flashplugin 11.2.202.400 and adobe-flash-properties-gtk 11.2.202.400 from the normal Ubuntu repositories. True for Ubuntu 12.04.5 and Ubuntu 14.04.1. - Whatever the trouble may have been with the packages for 11.2.202.394 is of no more relevance now.
Case closed.

---

