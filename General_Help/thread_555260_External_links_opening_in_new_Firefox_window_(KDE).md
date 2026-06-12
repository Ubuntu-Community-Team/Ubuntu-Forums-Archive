---
title: "External links opening in new Firefox window (KDE)"
date: 2007-09-19
forum: General Help
---

### Post by mivo on 2007-09-19
When I click on a link in KMail or any other application, a new Firefox window is opened. Expected (desired) behaviour would be that if Firefox is running, the link is opened inside a tab in the existing Firefox instance. My DE is KDE, the distro is Kubuntu 7.04.

This only affects "external" links. Links on pages displayed in Firefox open properly in new tabs (this seems to be a common problem, but it isn't the same as mine).

I looked around a bit, but haven't seen anything about this trouble. Any help is appreciated. :)

---

### Post by mivo on 2007-09-20
Several hours later, I found the solution.

Instead of putting "firefox"  in System Settings -> Default Applications -> Web Browser (that is what you get when you click on the "..." button and select Firefox from the menu), you have to put this in the field:

firefox -remote "openURL(%u,new-tab)"

This is absolutely not intuitive. ;) I found it here: [https://help.ubuntu.com/community/IntegrateFirefoxWithKDE]("https://help.ubuntu.com/community/IntegrateFirefoxWithKDE")

Only cost me half the night, but it works! Learned something new. :)

---

