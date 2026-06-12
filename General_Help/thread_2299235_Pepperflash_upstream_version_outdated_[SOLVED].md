---
title: "Pepperflash upstream version outdated? [SOLVED]"
date: 2015-10-16
forum: General Help
---

### Post by night_sky2 on 2015-10-16
Hi,

I have been trying to update pepperflash on my Xubuntu 14.04 installation but when I enter the terminal command:

sudo update-pepperflashplugin-nonfree --status

it says:

*Flash Player version installed on this system  : 19.0.0.***207**[I]
Flash Player version available on upstream site: 19.0.0.**1**[/I]**85**

How can the upstream source has fallen back to an older version?

BTW the latest version for Linux on Adobe's website is: 19.0.0.**226 **which fixes a major vulnerability found in the plugin.

Does anyone else is experiencing this?

---

### Post by Frogs Hair on 2015-10-16
Two ways to keep Pepperflash updated on Ubuntu include installing Chrome or using the Fresh Player PPA. If there is major security problem an update may come from the update manager. Flash was updated today, but I'm not using Pepper.

---

### Post by night_sky2 on 2015-10-16
> **Frogs Hair said:**
> Two ways to keep Pepperflash updated on Ubuntu include installing Chrome or using the Fresh Player PPA. If there is major security problem an update may come from the update manager. Flash was updated today, but I'm not using Pepper.
Yes, I use the Fresh Player ppa (Webupd8) but this does not install or update pepperflash. The Fresh Player Plugin is wrapper to make Google's pepperflash work in Firefox.

I am using the pepperflashplugin-nonfree package installed via terminal. I never had any issue with the update process before but now the upstream site is showing me an outdated version.

*Flash Player version installed on this system  : 19.0.0.***207**[I]
Flash Player version available on upstream site: 19.0.0.**1**[/I]**85**

---

### Post by Frogs Hair on 2015-10-16
The 3rd party PPA is subject to maintenance by the owner/s. I don't see an update for pepper on 15.10 yet.

---

### Post by night_sky2 on 2015-10-18
Marked solved. I uninstalled pepperflash the Fresh Plugin and went back to the NPAPI Adobe flash 11.2 for Firefox-based browers.

Not perfect but will do for the time being.

---

