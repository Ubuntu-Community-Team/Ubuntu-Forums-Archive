---
title: "Ubuntu 21.10 virtual desktop settings"
date: 2021-10-16
forum: General Help
---

### Post by Madpilot on 2021-10-16
On recent versions of Ubuntu prior to 21.10 your virtual desktops stacked "vertically", down from the primary desktop.

Especially if you run dual monitors this made intuitive visual sense. You had a left and right monitor and your virtual desktops stacked down from your primary monitor.

For inexplicable reasons 21.10 has decided that virtual desktops are now horizontally arranged, to the right of the primary monitor.

Has anyone found a setting to move virtual desktops back to the much more sensible vertical stacking used by previous Ubuntu releases?

Thanks!

---

### Post by deadflowr on 2021-10-16
You can thank gnome for completely changing a setup which worked well for what it was and did.
You'd probably need to check gnome extensions to see what has been created for the new gnome 40 desktop that Ubuntu 21.10 now uses.
Like this one: [https://extensions.gnome.org/extension/4144/vertical-overview/]("https://extensions.gnome.org/extension/4144/vertical-overview/")

Unfortunately firefox and chromium on Ubuntu 21.10 are default snap packages and do not properly work with the chrome-gnome-shell package (which is used for installing gnome extensions from a web browser.)
To install from a browser you'll need a browser built from a deb package.
Firefox does still have a deb version in the repos, so you can install that  in order to install the extensions you want.
(or any other non-snap browser should work)

---

### Post by Madpilot on 2021-10-16
I seem to have both a DEB and a snap version of firefox installed, both v93.0.(stuff) and I'm not actually sure how to tell which one I'm using right now.

I'm old school, I don't quite see the point of this snap/snapcraft nonsense when deb packaging and install was already a thing and super, super easy. And the fact that you can't easily tell which one you're actually using is an additional nuisance.

Anyway, in whichever version of Firefox I'm currently in, I installed the browser plugin and appear to have installed the dashboard extension - see screenshot below.


[ATTACH=CONFIG]289293[/ATTACH]

...but my virtual desktop is still sideways, and the options on the vertical overview extension are... opaque, to say the least, and do not appear to have any documentation.

---

### Post by Dennis N on 2021-10-16
If you don't want two versions of Firefox, you can remove the snap version:
```
snap remove --purge firefox
```
If you want both, you can rename one to tell them apart. You do that in the .desktop file in /usr/share/applications and edit the **Name=** line. That's what I did, at least for now.

---

### Post by monkeybrain20122 on 2021-10-16
> **Dennis N said:**
> If you don't want two versions of Firefox, you can remove the snap version:
```
snap remove --purge firefox
```
If you want both, you can rename one to tell them apart. You do that in the .desktop file in /usr/share/applications and edit the **Name=** line. That's what I did, at least for now.

Will the .deb version get updates? I just downloaded the tarball from Mozilla and tried it on Arch (gnome 4), it works quite seamlessly. Maybe all the packaging stuffs are not necessary.

---

