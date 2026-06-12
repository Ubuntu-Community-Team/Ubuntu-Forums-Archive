---
title: "Does this setup work?"
date: 2006-08-11
forum: General Help
---

### Post by SZF2001 on 2006-08-11
For ndiswrapper?

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/InstallDebian](http://ndiswrapper.sourceforge.net/mediawiki/index.php/InstallDebian)

Anyone tried it?

---

### Post by Jagot on 2006-08-11
Is there any reason you don't want to install ndiswrapper from the Ubuntu repositories?

---

### Post by az on 2006-08-11
If you installed using the Desktop cd, ndiswrapper-utils is on a repository on the cd, but apart from the live session.  Just boot into your installed ubuntu system and then insert the cd while at the desktop.  The package manager will start and you will be able to install ndiswrapper-utils.

---

### Post by SZF2001 on 2006-08-11
> **Jagot said:**
> Is there any reason you don't want to install ndiswrapper from the Ubuntu repositories?

Because it doesn't support WUSB11v4. Or maybe it does. But I can't get new versions of stuff with Breezy, and I am not in any hurry to update to 6.06... Unless the repositories have been updated or something. Have they?

---

### Post by SZF2001 on 2006-08-11
OK, how about this:

I'm still using Breezy, and ndiswrapper doesn't seem to be up-to-date according to Synaptic, so using WUSB11v4 drivers won't really work (I've tried it before).

So, how about I install [the wpa_supplicant package](http://hostap.epitest.fi/wpa_supplicant/) and the linux-wlan-ng package, could my WUSB11v4 driver possibley work?

---

### Post by az on 2006-08-11
Use this to set up your device:
[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb?highlight=%28prism2%29](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb?highlight=%28prism2%29)

To use ndiswrapper, you would have to blacklist the prism2_usb module from being loaded.  The version of ndiswrapper in Hoary was recent enough for prism2_usb devices...

You rarely need to get the latest version of ndiswrapper - just the most recent version of the inf file.  But use the native method as described in the wiki page.

---

### Post by SZF2001 on 2006-08-11
Are you sure that's gunna work? It says at the bottom I need to update.:(

---

### Post by az on 2006-08-11
It should work for breezy:
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111?highlight=%28netgear%29](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111?highlight=%28netgear%29)

---

