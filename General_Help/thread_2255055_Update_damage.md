---
title: "Update damage"
date: 2014-12-01
forum: General Help
---

### Post by Cyber72 on 2014-12-01
I installed some updates to 12.04 yesterday. Now I have some changes for the worse:
The icons in the launcher have become larger
The icons in dash have become smaller
Workspaces doesn't work anymore
I get the dog barking alert for no apparent reason.

Can I retrieve a list of the updates installed on a particular day?
Can I uninstall the culprit?
Why does this sort of thing happen?

---

### Post by Jonor on 2014-12-05
Try installing Synaptic Package Manager and then look at File > History to inspect what happened on different dates.
I should imagine there are better command line undo tools than this though.
You have been very unlucky to hit all that at once.

---

### Post by grahammechanical on 2014-12-05
You may have received an update/upgrade to Compiz the window compositor or to Unity that has reset everything to default values. Or you may have received an update/upgrade to a proprietary video driver that is causing a conflict and put Ubuntu into a standby video mode. In the case of Ubuntu 12.04 you maybe running Ubuntu 2D which does have large Launcher icons and which does not include a workspace switcher option. 

You can go to System Settings>Appearance and see if you can enable workspaces and resize the Launcher icons. If those options are not available it usually means we are using Unity 2D. So, then go to Additional Drivers and try changing video drivers.

Regards.

---

