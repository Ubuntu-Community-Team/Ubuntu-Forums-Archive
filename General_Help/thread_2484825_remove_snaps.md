---
title: "remove snaps"
date: 2023-03-11
forum: General Help
---

### Post by Old Jimma on 2023-03-11
Hello Forum:

My question is: > **What functionality is lost by removing all snaps?[**/QUOTE]

I removed the Firefox snap and replace it using a deb. ***_Firefox installed from a deb has more functionality that I needed._***

However, what are all of those other obscure apps doing? What should I replace them with??

Here is my snap list:

[QUOTE]
Name                       Version                     Rev    Tracking         Publisher   Notes
**bare**                       1.0                         5      latest/stable    canonical&#10003;  base
**core18**                     20230307                    2708   latest/stable    canonical&#10003;  base
**core20**                     20230207                    1828   latest/stable    canonical&#10003;  base
**gnome-3-28-1804**            3.28.0-19-g98f9e67.98f9e67  161    latest/stable    canonical&#10003;  -
**gnome-3-38-2004**            0+git.6f39565               119    latest/stable/…  canonical&#10003;  -
**gtk-common-themes**          0.1-81-g442e511             1535   latest/stable/…  canonical&#10003;  -
**snap-store **                3.38.0-66-gbd5b8f7          558    latest/stable/…  canonical&#10003;  -
**snapd**                      2.58.2                      18357  latest/stable    canonical&#10003;  snapd
**snapd-desktop-integration**  0.1                         49     latest/stable/…  canonical&#10003;  -
**wine-platform-6-stable**     6.0.4                       19     latest/stable    mmtrt       -
**wine-platform-runtime**      v1.0                        338    latest/stable    mmtrt       -


I noticed that there are gnome snaps... and I use gnome extensions. I wondered if it is really safe for me to remove the gnome snaps, for example.

But, what do bare, core, and wine do? Is it really safe to remove them???

Thank you!

Old Rotted Jimma from the 'Hood

---

### Post by deadflowr on 2023-03-11
Perfectly safe to remove all snaps, 

The gnome snaps have no affect on the system outside of being used by the other snaps.
Snaps in general are restricted so they do not have full access to the system.
The gnome and gtk snaps allow the snaps to function as if they do.
It's more complicated than that, but that's the basic idea, more or less.

The core, bare and wine snaps are runtime snaps, in general.
Those allow snaps to actually run.

---

### Post by grahammechanical on 2023-03-12
You may find that if you remove the snap-store snap packaged application that you lose the Ubuntu Software application. I think that Ubuntu Software is in fact what used to be the Snap Store.

If you remove snapd then snap applications will not work. I have the deb version of Wine installed and I do not have any Wine related snaps. I am not aware that Wine has been snap packaged. Ubuntu Software on Ubuntu 23.04 (development version) offers the deb version of Wine as do Ubuntu 20.04 and WineHQ web site. This is where those Wine snaps came from:

[https://snapcraft.io/install/wine-platform-runtime/ubuntu](https://snapcraft.io/install/wine-platform-runtime/ubuntu)

This will explain things. Maybe.

[https://askubuntu.com/questions/1369464/auto-installed-wine-ubuntu-20-04](https://askubuntu.com/questions/1369464/auto-installed-wine-ubuntu-20-04)

Regards

---

### Post by Old Jimma on 2023-03-12
thank you grahammechanical:

I think I'll leave things as they are and be happy that I deleted the Firefox snap and found a Firefox deb that has more features to replace it.

Take care,
Old

---

