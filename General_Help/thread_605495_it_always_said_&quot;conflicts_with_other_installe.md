---
title: "it always said &quot;conflicts with other installed software&quot; what can I do?"
date: 2007-11-07
forum: General Help
---

### Post by stevenfish on 2007-11-07
I want to install 'gdesklets' from add/remove... in the Applications menu,but it showed me such message below:

Cannot install 'gdesklets'

This application conflicts with other installed software. To install 'gdesklets' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

-------------------------
I know is the conflicting,but how can I know which software is conflict with 'gdesklets'? 

Please give any ideas will  be fine,cheers:(

---

### Post by mpierce on 2007-11-07
Try sudo apt-get install gdesklets
when it fails as it probably will given what you have said, try

sudo apt-get -f install 

This will try to correct any dependencies and will either ask if it is ok to remove software so that it can install gdesklets or, simply remove gdesklets since it can not install it.

gdesklets says that it only runs on a ubuntu desktop and not kubuntu.

Hope this helps...

---

