---
title: "Can ndiswrapper be used with Vista drivers?"
date: 2007-03-26
forum: General Help
---

### Post by dwasifar on 2007-03-26
I have a new Toshiba laptop on which I'm trying to get the Atheros wireless to work, and am having no luck.  I think it's a driver issue.  It can see the local networks but can't successfully connect to any of them, WEP or open, doesn't matter.  I've tried various flavors of Ubuntu (Edgy, Kubuntu Edgy, and Kubuntu Feisty) to see if the native support works; I've also tried the latest release candidates of PCLinuxOS and SimplyMepis.  No distro seems to have the appropriate configuration to make it work.

So now I'm thinking of ndiswrapper, but the only drivers available from Toshiba are for Vista only, and I can't find drivers anywhere else yet.  Can I use ndiswrapper with the Vista drivers?

---

### Post by CocoAUS on 2007-03-26
It might be a driver issue, or it mights imply be a network issue.  Using ndiswrapper, I was able to see all the local networks, but could only connect to one of them consistently--and it wasn't mine.  Feisty's gotten my card to work with bcm43xx almost out-of-the-box now, so I don't worry about it anymore, but from my experience with ndiswrapper, I wouldn't put too much hope in it.

There's no harm in trying it out, though.  Using ndiswrapper is a pretty straightforward process, and if it doesn't work, you don't even have to uninstall anything if you don't want to.

---

### Post by kevmitch on 2008-02-20
I've got an Atheros AR5418 chip and contrary to CocoAUS's experience, I have found ndiswrapper not only to work well and reliably, but to be the only thing that works well and reliably. Madwifi is a disaster as far as this card is concerned. 

Unfortunately, ndiswrapper does not yet support Vista drivers, so you have to find an XP driver to get it to work. I found mine for the above chipset on the Lenovo website. Here's the howto with a link to the driver: [http://www.thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter](http://www.thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter)

Of course that driver won't do you any good if you don't have the AR5418. In order to find out your chipset, run the commands:
update-pciids
lspci | egrep -i 'network|atheros|wireless'
and google around for the relevant chipset. Though there may not be a driver for your card specifically, I find it hard to believe that Atheros doesn't have an XP driver for this chipset somewhere.

---

