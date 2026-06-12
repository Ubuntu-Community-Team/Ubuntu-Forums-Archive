---
title: "Ubuntu 21.04. Does apt update and apt upgrade work on all apps?"
date: 2021-08-06
forum: General Help
---

### Post by Advait on 2021-08-06
[COLOR=#000000][FONT=Arial]Newbie here. About 3 weeks ago I switched from Windows 10 to Ubuntu 21.04. Occasionally I do &#8216;sudo apt update&#8217; and &#8216;sudo apt upgrade&#8217;. Does this update/upgrade all my apps? If not, how can I tell which apps are not getting updated/upgraded?
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I want to keep all my apps up to date. I have installed a few snaps, flatpaks and appimages. I&#8217;ve also downloaded and and installed some .deb files.[/FONT][/COLOR]

---

### Post by mikewhatever on 2021-08-06
Nope. Flatpacs and appimages are not covered by apt, also, anything installed from source or stand alone debs. Snap packages are autoupdated.

---

### Post by Advait on 2021-08-06
> **mikewhatever said:**
> Nope. Flatpacs and appimages are not covered by apt, also, anything installed from source or stand alone debs. Snap packages are autoupdated.

Thanks. Very helpful. Now I can make a list of my apps that need manual updating.

---

### Post by guiverc on 2021-08-06
If you install .deb files locally (ie.
- `dpkg -i` or 
- `apt install ./*[package]*.deb`
without adding a source to your system, they'll also get skipped (ie. *need manual upgrade*) as the system has to know where to look to look for updated packages; ie. adding a source to 
- /etc/apt/sources.list or
- placing it in /etc/apt/sources.list.d/

(otherwise what I said on [https://askubuntu.com/questions/1356311/ubuntu-21-04-does-apt-update-and-apt-upgrade-work-on-all-apps;](https://askubuntu.com/questions/1356311/ubuntu-21-04-does-apt-update-and-apt-upgrade-work-on-all-apps;) ie. `apt upgrade` can leave some packages behind where removal is required)

---

### Post by grahammechanical on 2021-08-06
It is true that snap applications are automatically updated but only if we are updating using the Software Updater utility. Otherwise we run this command

```
sudo snap refresh package_name
```

Regards

---

### Post by Advait on 2021-08-07
Thanks everyone for all the details. It all helped me understand app  updating and helped me create a cheat sheet of the various classes of  apps and how they get updated.

---

### Post by deadflowr on 2021-08-07
> **grahammechanical said:**
> It is true that snap applications are automatically updated but only if we are updating using the Software Updater utility. Otherwise we run this command

```
sudo snap refresh package_name
```

Regards

Snaps do not require any user intervention as they auto update.
You also never need to run any snap commands with sudo as they have builtin authentication.

As far as I know the snapd service runs update checks at least twice daily.
With some snaps have updating policies for themselves with even more update checks.
(Snaps like canonical-livepatch run an update check hourly)

Snap updates that come through during a regular software-updater are basically updates that have come since the last snap refresh check was run by the snapd service. But if you never run software updater those snap updates would come all on their own.


On another note flatpak do not have the same update mechanism that snaps have, but you can set them to using gnome-software.
An old thread on that here: [https://ubuntuforums.org/showthread.php?t=2446274]("https://ubuntuforums.org/showthread.php?t=2446274")

Then as far as appimages go I believe there are appimage updater utilities like this 
[https://appimage.github.io/AppImageUpdate/]("https://appimage.github.io/AppImageUpdate/")

And then, of course, any package installed from sources which have no repository or some other updating function will require manual updating.

---

### Post by Advait on 2021-08-08
> **deadflowr said:**
>  Then as far as appimages go I believe there are appimage updater utilities like this 
[https://appimage.github.io/AppImageUpdate/](https://appimage.github.io/AppImageUpdate/)

Thanks for the tip. I installed Appimageupdate.

---

