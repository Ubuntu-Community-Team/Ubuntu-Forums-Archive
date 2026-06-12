---
title: "Problem in installing unity-control-center"
date: 2017-07-01
forum: General Help
---

### Post by esolve3 on 2017-07-01
My "System Settings" doesn't work and I notice it is because I carelessly uninstalled "unity-control-center", now I want to reinstall it,  but I get dependency problems:


        $ sudo apt-get install --reinstall unity-control-center
        [sudo] password for nanger:
        Reading package lists... Done
        Building dependency tree
        Reading state information... Done
        Some packages could not be installed. This may mean that you have
        requested an impossible situation or if you are using the unstable
        distribution that some required packages have not yet been created
        or been moved out of Incoming.
        The following information may help to resolve the situation:


        The following packages have unmet dependencies:
         unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                                Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
        E: Unable to correct problems, you have held broken packages.


I want to install libcheese-gtk23 and libcheese7 , but they then again depends on other unmet dependencies, and this loop turns to be endless, what can I do?


-----------------------
FYI:


        $ sudo apt-get install --fix-missing
        Reading package lists... Done
        Building dependency tree
        Reading state information... Done
        The following packages were automatically installed and are no longer required:
          apg cups-pk-helper gkbd-capplet libcolord1 libgnome-desktop-3-7 libgnomekbd8
          libgtop2-7 libtimezonemap1 ubuntu-system-service
        Use 'sudo apt autoremove' to remove them.
        0 upgraded, 0 newly installed, 0 to remove and 19 not upgraded.

---

