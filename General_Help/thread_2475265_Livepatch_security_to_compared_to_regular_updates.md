---
title: "Livepatch security to compared to regular updates"
date: 2022-05-20
forum: General Help
---

### Post by cam17 on 2022-05-20
What does livepatch give you in terms of updates for Ubuntu apps and system updates? If a user uses only regular updates what is the security risk?

---

### Post by Holger_Gehrke on 2022-05-20
Livepatch updates the currently running Kernel in memory. It's meant for systems which are not supposed to go down even for a few minutes for a reboot into a new kernel. Think '99.99 % Availability of Service' kind of things.

Holger

---

### Post by #&amp;thj^% on 2022-05-20
> **Holger_Gehrke said:**
> Livepatch updates the currently running Kernel in memory. It's meant for systems which are not supposed to go down even for a few minutes for a reboot into a new kernel. Think '99.99 % Availability of Service' kind of things.

Holger

+1

@cam17 have a look:[https://ubuntu.com/security/livepatch/docs](https://ubuntu.com/security/livepatch/docs)

---

### Post by Impavidus on 2022-05-21
With a kernel upgrade on average once every two weeks and a shutdown-reboot cycle taking less than 2 minutes, you can already get 99.99% availablitity without livepatch.

---

### Post by cam17 on 2022-05-29
RIght now I do not use live patch. When I get an update it shows the updates to be applied. does live patch just update the system with no notification?

---

### Post by deadflowr on 2022-05-30
> does live patch just update the system with no notification?
It installs the updates without any user interaction required.

You can set it to show a status indicator for it in the top panel of the Ubuntu desktop.
Which should show if any new patches have been applied or not.
I know this applies to the Ubuntu desktop, but I am not sure about the various flavor desktops.

I also see that the indicator might be broken on Ubuntu 22.04:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-appindicator/+bug/1969855]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-appindicator/+bug/1969855")

---

