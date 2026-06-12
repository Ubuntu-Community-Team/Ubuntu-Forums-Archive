---
title: "Firefox/Swiftfox Crashes Randomly Error"
date: 2008-03-04
forum: General Help
---

### Post by mastercomputerwizard on 2008-03-04
Firefox and Swiftfox are crashing while browsing. I ran them in a terminal and have captured the following error.

$ swiftfox
LoadPlugin: failed to initialize shared library /usr/lib/firefox/plugins/libunixprintplugin.so [libxpcom_core.so: cannot open shared object file: No such file or directory]
Segmentation fault (core dumped)

Any ideas???

---

### Post by talsemgeest on 2008-03-04
I suggest reinstalling firefox and swiftfox

---

### Post by mastercomputerwizard on 2008-03-04
Already have done that....Thank you for the suggestion.

Have also reinstalled flash and java.
Ran in safe mode and they still will crash.

This problem is not one machine independent. I have three boxes running Ubuntu 7.10 and Firefox/Swiftfox will crash on them all with the same combination of pages being open.  The only thing they have in common is they are running multiple monitors with the latest Nvidia drivers. 
Note:Crashed on the older Nvidia drivers also so I would say it is safe to rule out the video drivers.

Can some one tell me what package/program that the (/usr/lib/firefox/plugins/libunixprintplugin.so) plugin  belongs to????

---

### Post by talsemgeest on 2008-03-04
I'm guessing that it gives the printing support for firefox

---

### Post by mastercomputerwizard on 2008-03-04
I figured it had to do with printing since that is in the description. 
However I am thinking it has to do with a specific plugin that needs re-installed or updated.
I am trying to figure out what file/package that plugin belongs too.  
Once that is discovered that may solve a bunch of the other tickets out there that are having random crashes that has not found a specific fix for this problem yet.

---

### Post by talsemgeest on 2008-03-04
Still guessing that it came installed with firefox, since it is kind of essential to be able to print. Reinstalling firefox would be the only way to fix that if that was the case

---

