---
title: "How to fix compiz and unity not launching."
date: 2013-01-18
forum: General Help
---

### Post by jimmytbane on 2013-01-18
After ubuntu moved to unity, some bugs came along with it. Unity is responsible for menus and application launchers in ubuntu. Once one logs in to their computer, there are no menus or window borders. In order to fix this you need to launch terminal, (ctrl + alt + T). Once you have done so. Type "sudo apt-get install synaptic" without quotes. it will ask for a password and then install the synaptic package manager. once this has been installed it can be launched through the command "sudo synaptic". Once synaptic package manager has opened. There will be a search field in the mid-upper right corner. type linux-headers-generic. and right click to the option "mark for installation" then go to apply and once it has completed you may restart. Likely you will now have proper dependencies and unity will work.

PS: If something doesn't work, please tell me.

---

### Post by UT_Libertarian on 2013-02-15
Had unity quick launch this morning, this evening it's gone.  How do I re-enable it?

---

