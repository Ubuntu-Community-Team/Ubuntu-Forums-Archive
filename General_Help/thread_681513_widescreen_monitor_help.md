---
title: "widescreen monitor help?"
date: 2008-01-29
forum: General Help
---

### Post by symon1980 on 2008-01-29
Hi, i have an LG Flatron l192ws and i have ubuntu gutsy gibbon. I never had this problem with my older lcd, but since getting my new lcd, whenever i load ubuntu i get a message saying 'out of range' blah blah, it sits there for about 20 seconds, and after that everything is fine. Its just annoying because it takes forever to load up ubuntu. I have the correct resolution set 1440/900, and i have tried other resolutions and have had the same problem. Any suggestions?
thankyou :)
regards
symon.

---

### Post by quoderat on 2008-01-29
Hi there. If you are using the Nvidia drivers, here's how you should be able to get it to work. Put this line under the Device section of your xorg.conf file:

Option "UseEDID" "False"

With the quotes and everything, just as is. Hope this helps.

---

