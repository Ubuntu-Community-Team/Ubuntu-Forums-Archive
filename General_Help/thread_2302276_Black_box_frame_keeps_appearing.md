---
title: "Black box/ frame keeps appearing"
date: 2015-11-09
forum: General Help
---

### Post by UncleMonty on 2015-11-09
For some reason a black box/ frame keeps appearing - here is a screenshot of what it looks like. I'm using ubuntu 14.04 LTS and unity. Any ideas what can have caused this? (It also appears when using the search bar, address bar, etc)

---

### Post by yetimon_64 on 2015-11-09
> **UncleMonty said:**
> For some reason a black box/ frame keeps appearing - here is a screenshot of what it looks like. I'm using ubuntu 14.04 LTS and unity. Any ideas what can have caused this? (It also appears when using the search bar, address bar, etc)

Also on 14.04/Unity here and I occasionally get an identical border around any windows. I've found restarting the display manager "lightdm" with the command "sudo service lightdm restart" from a tty terminal and re-logging in to the session will reset it.

How often do you get the effect ? My set up only does it occasionally, it is not a consistent fault here.

What video hardware and drivers are used/installed ? Have you installed any proprietary drivers from nvidia/amd or from any PPAs (like the "xorg-edgers" PPA) etc ? 
For instance I get the effect here using nvidia 349.16 drivers on a hybrid intel/nvidia card using the xorg-edgers PPA but can reset it from a tty terminal with the "sudo service lightdm restart" command.

---

### Post by UncleMonty on 2015-11-09
> **yetimon_64 said:**
> Also on 14.04/Unity here and I occasionally get an identical border around any windows. I've found restarting the display manager "lightdm" with the command "sudo service lightdm restart" from a tty terminal and re-logging in to the session will reset it.

How often do you get the effect ? My set up only does it occasionally, it is not a consistent fault here.

What video hardware and drivers are used/installed ? Have you installed any proprietary drivers from nvidia/amd or from any PPAs (like the "xorg-edgers" PPA) etc ? 
For instance I get the effect here using nvidia 349.16 drivers on a hybrid intel/nvidia card using the xorg-edgers PPA but can reset it from a tty terminal with the "sudo service lightdm restart" command.


Thanks I'll make a note of that commmand.

First time it's happened, thought I should nip it in the bud. 

I've absolutely no idea - how can I check please?

---

