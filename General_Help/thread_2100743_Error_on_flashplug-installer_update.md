---
title: "Error on flashplug-installer update"
date: 2013-01-02
forum: General Help
---

### Post by Ralph L on 2013-01-02
I am installing Ubuntu Precise Pangolin 12.04.1.  I installed from the live CD and then invoked Update Manager to get the latest.  It completed, but left a window stating that it couldn't complete installation  of flashplugin installer.  This is part of the message; I lost the other part:  "flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.258.orig.tar.gz"

Using synaptic I tried to do a reinstallation of flashplugin-installer.  It failed to complete leaving the following in the synaptic window under Details: "Setting up flashplugin-installer (11.2.202.258ubuntu0.12.04.1) ...
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)".

Flash isn't working.  I can't run [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/) , which requires flash.

Any help on how to get synaptic to complete the flash installation would be appreciated.

---

### Post by GregA on 2013-01-10
Hello,

I too have seen a regular failure to update the flash plugins, whenever updates show in apper or other package mgmt notifiers.

What I've had to do is use synaptic to completely uninstall flash, and then reinstall.  That's worked each of the 5 or 6 times in the past few months were system updates would break flash.

It seems the /var/cache/apt/archives folder could not be written to . . perhaps another forum member has a better faster or more permanent method to fix this.

I've attached a jpeg of the consistent error message I get in Synaptic if I just try to to an update (versus an uninstall-reinstall).

Hope this helps.

---

