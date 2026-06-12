---
title: "Failed Gui Launch: likely bad nvidia driver plus 404 errors on impish release repo"
date: 2023-07-02
forum: General Help
---

### Post by jhunt89 on 2023-07-02
My Ubuntu 21.10 desktop with nvidia drivers will not launch the graphical login manager.  When my monitor is plugged into my nvidia card, I can't even ctrl+f key to a different virtual console.  When plugged into the built in intel graphics, graphical login does not launch, but I can get to a virtual console to attempt troubleshooting.  This seems like a common enough problem, and I found [https://support.system76.com/articles/login-loop-ubuntu/](https://support.system76.com/articles/login-loop-ubuntu/) for troubleshooting.

However, I cannot update/upgrade the system, let alone reinstall various drivers, because the repos for impish release 404.  So it seems I've ran into a bit of a perfect storm of issues.  I let the machine sit for quite some time before returning to it, unfortunately.

Looking for assistance on where to go from here.

Thank you,
Josh

---

### Post by ajgreeny on 2023-07-02
The first comment, and really the only important one is to tell you, as you appear to know already, that Ubuntu-21.10 is now totally unsupported so you will not have received any system or security updates for about a year now making your OS very insecure.

Please update or clean install a newer and fully supported version; I would recommend Ubuntu-22.04 (or your choice of other DE version, eg Xubuntu, Kubuntu, etc).
It will probably be much easier to clean install 22.04 rather than upgrade but ensure you have all your own personal folders and files from your current home backed up first so you can restore them if anything goes wrong.
You can also try an online upgrade of the EOL 21.10 by trying the method shown at [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) which I have never attempted; I have never done this when the OS is still supported, always clean installing.

---

### Post by jhunt89 on 2023-07-02
I took your advice and opted for backup + clean install.  Thank you much for the fast response!

---

