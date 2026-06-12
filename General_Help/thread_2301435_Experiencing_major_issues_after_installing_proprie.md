---
title: "Experiencing major issues after installing proprietary graphics driver"
date: 2015-11-02
forum: General Help
---

### Post by mejl on 2015-11-02
Hello! I thought it was a good idea to install the AMD Radeon graphics driver from the official AMD Radeon website, turned out it wasn't - on reboot I faced the purple screen of death. I decided to reinstall Ubuntu (used the entire disc for my new installation) but now an issue with my network controller has occured plus I can't change the display resolution. Also, it takes forever to boot UEFI and Ubuntu, it used to take 10 seconds, now it's more like 5 minutes of blank screen (no signal) before UEFI and then Ubuntu boots. Any and all help appreciated.

---

### Post by DK1993 on 2015-11-02
Hi mejl. Were you trying to install the Radeon drivers on a Ubuntu 15.10 installation? If so, this is a known and documented bug. From Ubuntu's Release Notes ([https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes#Known_issues](https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes#Known_issues))

> [COLOR=#333333][FONT=Ubuntu Beta]AMD's [/FONT][/COLOR]**fglrx**[COLOR=#333333][FONT=Ubuntu Beta] driver does not work with the current kernel ([/FONT][/COLOR][1493888]("https://bugs.launchpad.net/bugs/1493888")[COLOR=#333333][FONT=Ubuntu Beta]). It is warmly recommended to uninstall the fglrx driver before upgrading to Ubuntu 15.10. The open source "radeon" driver can be used as a temporary replacement until a fix is available. [/FONT][/COLOR]

if this is the case I'd recommend installing Ubuntu 14.04 LTS until this is resolved.

---

### Post by mejl on 2015-11-02
I'm not 100% certain if it was 15.04 or 15.10. However, my fresh 15.04 install doesn't detect my network controller (ethernet) and since I'm unable to change my display resolution I think something's wrong with that driver also. Plus it takes forever to boot Ubuntu (or UEFI) all of a sudden. It all seems to have a connection to the graphics driver which is now uninstalled but might still be haunting my system. Any suggestions?

---

