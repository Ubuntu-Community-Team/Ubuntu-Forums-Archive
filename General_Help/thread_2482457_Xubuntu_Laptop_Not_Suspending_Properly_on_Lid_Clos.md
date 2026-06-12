---
title: "Xubuntu Laptop Not Suspending Properly on Lid Close"
date: 2022-12-31
forum: General Help
---

### Post by Spiralagnus on 2022-12-31
I have a Dell Latitude 5580 laptop running Xubuntu 22.04, and the laptop does not suspend when the lid closes. Based on other research, here's what I've tried so far:

 - Made sure the "Suspend" option is chosen for "When laptop lid is closed" in the Power Manager.
 - Installed pm-utils.
 - Ran the following command: ```
xfconf-query -c xfce4-power-manager -p /xfce4-power-manager/logind-handle-lid-switch -n -t bool -s false

```
Interestingly, when I use logind to suspend on lid close, the laptop does suspend properly, but the desktop is frozen when I open the computer back up.

I'm not sure where to go next. I'd appreciate any advice the community can provide. Thanks!

---

