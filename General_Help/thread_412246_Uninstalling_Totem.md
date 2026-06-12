---
title: "Uninstalling Totem"
date: 2007-04-17
forum: General Help
---

### Post by kotty1216 on 2007-04-17
I installed VLC with another forum post so I could play DVD's on Linux, but now I was wondering if there was a way to uninstall Totem which came on my Ubuntu Install. I tried using the generic uninstaller (not the synaptic one) and it gave me an error saying that one or more applications are dependant on it. I haven't used synaptic, because I don't know what to look for when search for totem. If anyone can help that would be great.

---

### Post by Zwalther on 2007-04-17
When you search for totem in synaptic, it should list totem in the right hand side. You can click on the green square and select uninstall. It might want to uninstall some other packages too then.

I would recommend to leave totem installed and configure vlc as your default dvd player. You can set that somewhere in System->Preferences->Devices and Multimedia. I'm currently at work, so I'm not sure.

---

### Post by thephotoman on 2007-04-18
Uninstalling Totem might not be a good idea.

While it won't cause breakage now, when it comes time to upgrade your system, it can cause headaches.  Simply put, one thing that people have learned in the past is that it helps to have ubuntu-desktop installed during the upgrade process.  Totem is a part of ubuntu-desktop.

No, what you really want is the default behavior upon inserting a DVD to change.

To change this, go to System > Preferences > Removable Drives and Media, select the "Multimedia" tab, and then change the command under "Video DVD Discs" from "totem %m" to "vlc".

---

### Post by kotty1216 on 2007-04-18
Alright I'll do that then. Thanks for your help.

---

