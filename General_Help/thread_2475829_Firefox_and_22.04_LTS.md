---
title: "Firefox and 22.04 LTS"
date: 2022-06-09
forum: General Help
---

### Post by Robbyx on 2022-06-09
I have been holding back upgrading from 20.04 LTS because I use Firefox. I held back because I did not want to face the muddle and complication evidenced by this April 2022 discussion involving FF,  Snap and Apt and the reversion to a prior release:

[https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/](https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/)

Has the position changed since April?

---

### Post by Dennis N on 2022-06-09
> Has the position changed since April? 

Some of that reference is no longer correct:
> Snap is OK. But when you trying to install Gnome Extensions, the browser doesn&#8217;t work at the moment! So, you need workarounds:

    Firefox Linux tarball from Mozilla website
    Firefox ESR PPA.
    Firefox PPA.
    Ubuntuzilla repository

This objection is no longer valid. You don't need a web browser to install gnome-shell extensions from the extensions web site. Install the utility "Extensions Manager" (gnome-shell-extension-manager) and you install and manage extensions with that. 

A .deb package is not the only option for Firefox. It is also available as a Flatpak package. It's faster to launch than the Snap. I use the Flatpak version of Firefox myself since I am into using Flatpaks for other packages as well when I want to run the latest stable versions, and avoid PPAs.

---

### Post by Robbyx on 2022-06-09
Thank you for making the position clear.

---

### Post by mikewhatever on 2022-06-09
Upgrdes from 20.04 to 22.04 won't be available until July/August 2022, so you might need to hold back a bit longer regardless of Firefox.

---

### Post by Robbyx on 2022-06-09
Noted and thanks

---

### Post by vanadium on 2022-06-10
> **Dennis N said:**
> I use the Flatpak version of Firefox myself since I am into using Flatpaks for other packages as well when I want to run the latest stable versions, and avoid PPAs.
The bug, where a file dialog ("Open" or "Save") does not have keyboard focus when you launch it a second and subsequent times during a session probably is not solved yet, but very few people seem aware of this bug. It is, however, annoying for people with a keyboard based workflow.

(ps. this does also apply for snap and appimage, it is an xdg-portal issue)

---

