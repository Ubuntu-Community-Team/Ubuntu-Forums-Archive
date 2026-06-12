---
title: "Adoble Flash in Ubuntu (32 bit) (How do I get it?)"
date: 2007-12-03
forum: General Help
---

### Post by s3a on 2007-12-03
I wanted to send an ecard and Firefox led me to Adobe's Flash things and I downloaded the .RPM one and used alien to convert it to a .deb and then installed but I can't view the ecard still! What am I doing wrong? Is there any "real" .deb that I am not aware of?

---

### Post by PeterJS on 2007-12-03
First enable the universe and multiverse repositories as shown here:
[https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

Then open up synaptic and install: *Flashplugin-nonfree*

---

### Post by dasunst3r on 2007-12-03
On Gutsy, the plugin installation routine has significantly improved to the point where you really should not have done that.  In any case, use Synaptic to uninstall the package you install and try going to the Flash-enabled site again.

+1 for previous post.

---

### Post by mikewhatever on 2007-12-03
Go to a site that requires flash. You'll be prompted to install a missing plugin. Install it and you are done. Another way is to install flashplugin-nonfree package from the repositories.

---

