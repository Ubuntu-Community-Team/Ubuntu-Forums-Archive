---
title: "no update message: &quot;Requires installation of untrusted packages&quot;"
date: 2013-05-10
forum: General Help
---

### Post by DrScum on 2013-05-10
When trying to update using the update manager I get the message: "Requires installation of untrusted packages"
the following packages are mentioned under "details"

gnome-keyring handbrake-gtk icedtea-6-jre-cacao icedtea-6-jre-jamvm libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2 libgck-1-0 libgcr-3-1 libgcr-3-common libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglu1-mesa libnm-gtk-common libnm-gtk0 libpam-gnome-keyring libssl1.0.0 libunity-2d-private0 libxatracker1 network-manager-gnome openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openssl unity-2d unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread

how can I fix this?

---

### Post by grahammechanical on 2013-05-10
Update Manager is only asking you to take responsibility for downloading and installing those packages. If we install software through Personal Package Archive (PPA) then we get a message like that. Have you not noticed when installing applications through the Software Centre that many of them will carry a warning that they will not be updated by Canonical, that some updates may come from the Community. It is these kinds of updates that you are being asked to approve of.

Go to System Settings>Software Sources>Ubuntu Software and uncheck Community-maintained free and open source software (universe) and then go to Other Software tab and uncheck any PPAs that are there. And the nasty message will go away. Or just authenticate the download and installation.

Regards.

---

### Post by DrScum on 2013-05-10
How would I "authenticate" the download and installation?

By the way, if I go to System Settings, there is no "Software Sources" available. The only place where I can check and uncheck repositories is in the synaptic package manager. Isn't it true that when I uncheck the sources as you suggest that I won't be prompted to upgrade anymore? That's not what I want, I want to stay up to date with my software but the way it is now the update manager won't let me do it.

---

### Post by oldos2er on 2013-05-10
Usually you see that error message because you're missing one or more gpg keys; see  [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)
If you run ```
sudo apt-get update
``` in a terminal it should show which repositories are missing keys.

---

### Post by DrScum on 2013-05-10
Thanks Ann, the terminal command sudo apt-get update didn't tell me anything about missing keys but after I ran that command, the update manager works without the initial error.

---

