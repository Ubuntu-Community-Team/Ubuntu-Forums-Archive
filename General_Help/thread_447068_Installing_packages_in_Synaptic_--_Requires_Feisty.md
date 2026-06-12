---
title: "Installing packages in Synaptic -- Requires Feisty cdrom???"
date: 2007-05-17
forum: General Help
---

### Post by briansalo on 2007-05-17
Hello all,

I just installed Ubuntu Studio yesterday, and am having an issue with installing packages in Synaptic (I need ndiswrapper for my wireless to work).. I click to install the packages and it wants me to put in the Feisty 7.04 cdrom... I only have a Ubuntu Studio disc which doesn't work...  If anyone has a way to change this so I wouldn't have to do this would be greatly appreciated.

---

### Post by hsweet on 2007-05-17
Not really, you just gotta remove it from the software sources (repository ) list.  You can do that with the /system/software sources menu item or editing the /etc/apt/sources.list file.  Either way, uncheck the cd  or comment out the text for the cdrom.

---

### Post by briansalo on 2007-05-17
Actually, I solved the problem on my own...

For anyone who was wondering, in the settings>repository menu... one of the cdrom options was chosen as a source for installing... deselecting that will fix the problem.

EDIT: You beat me to posting hsweet... but thankyou for your help with this :D

---

