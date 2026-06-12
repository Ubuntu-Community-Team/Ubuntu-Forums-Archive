---
title: "Why 2 software stores for the same Software?"
date: 2021-05-26
forum: General Help
---

### Post by dddman on 2021-05-26
SoftwareStore/UbuntuStore; does it matter which one is used?

[ATTACH=CONFIG]288553[/ATTACH]

And then there's Snapcraft flying the same banner.

I find places like this helpful:
[https://www.linux-apps.com/browse/cat/](https://www.linux-apps.com/browse/cat/)

---

### Post by TheFu on 2021-05-26
Don't think those are any different on the back-end.
Thinking about the question a bit more, I can see Canonical wanting snaps to be used on other distros (Chromium is only available officially as a snap), so having an unbranded GUI to load/delete/update software is helpful for Arch, Fedora, and other distros.  Of course, inside any Ubuntu release, having it branded as "UbuntuStore" makes sense.  Check where the repos point, that's the only way to really know.

There are multiple locations for software due to historic reasons.

**APT** - repos.  This is what we've used since the 1990s. Different repos can be added/included. It is possible to include "PPAs" to fully integrate 3rd party software into APT.  sudo apt update/sudo apt upgrade are how to patch.  Each repo is specific to a distro and specific release. Dependency management is handled by using matched repos.

**AppImages** - these are an attempt at "package-once, run on any Linux" packages.  The packages include most dependencies, so they can become huge. I don't know who sponsors it.  A program that is 32MB, when packaged can be 950MB - so a 30x size difference. That is an extreme example for a Qt-based program on a system with GTK+ base.  AppImages have no automatic update/patch capability. That's good and bad.

**Flatpaks** - Similar to AppImages, but with some added protections for containment. Constraints that are default in the package can be locally overridden if the system requires it. Redhat is the sponsor, but it is popular outside the RH distros.  The package sizes are huge, if the dependencies need it. s 32MB, when packaged can be 950MB - so a 30x size difference.  Flatpaks can be updated using the update/patch facility. I have little experience with flatpaks.

**Snap** Packages - Similar to Flatpaks, but without the ability to override the package maintainer constraints.  By default, snaps don't allow access for data outside the HOME directory for the user.  Some snap-packages can be asked to allow access to storage under /mnt/ and /media/, but nowhere else. Snaps also do not work over networked storage, so CIFS and NFS and sshfs don't work.  SnapStore is sponsored by Canonical.  Snaps have a package size problem just like the others. Snaps have broken out the dependencies to finer levels, which can be helpful.  They've basically re-invented APT dependencies, but with constraints - some excellent, some terrible.  Snaps are automatically updated. 2-3 copies of the same tools are kept on the system, so if a package needs 140MB, then it will use 435MB of storage unless manual action is taken.

So ... in recent Ubuntu releases, Canonical has been trying to push Snap packages and has been merging the idea of a software store that includes both APT and Snap packages.  The lists in these storage is drastically reduced compared to what is actually in the repos. I'd guess it is to have a curated selection of software and limit confusion by non-technical people.  If you'd like a GUI and want to see all the APT packages, check out Synaptic.  **Synaptic** was the default software package manager in Ubuntu for a few years. Synaptic does NOT know anything about snaps. Currently, there are over 50K packages listed in APT.  Also, for users that are disconnected from the internet, synaptic can create download scripts to get packages and the dependencies from another system.  Snaps allow downloading offline, but I think it doesn't allow the validation, so may not allow the package to be installed. Snaps really want a system to be internet connected. 

I could be wrong.

The term "store" doesn't really apply.  Almost all software that end-users would like to use are F/LOSS, with just a few exceptions.  The snapstore run by Canonical is the only one, that exists. Walled-garden?

---

### Post by grahammechanical on 2021-05-26
I do not think that there are two software stores. Just two different icons loading the same application. Unlike you I am unable to pull up an "about" option to reveal what application it is. But from reading the "About" dialogs you see it is apparent that they are in fact the same application.

Open Software and tick Installed>System Applications and look for Software. It is Gnome Software. I do not see Ubuntu Software when I do this. 

Now open Ubuntu Software Installed>System Applications. Again we see Software and it is Gnome Software but I do not see Ubuntu Software.

Strangely, I do see a Snap Store in both Software & Ubuntu Software. My 20.04 is an upgrade from at least two previous LTS versions. In those days we had a separate Snap store. But there is now better integration in Software for Snaps and Flatpacks than before. If I launch Snap Store from Software I get Software and not a different application. Which is what was happening a few years ago.

What is peculiar is that we get two different designs of Icons in the Grid. I guess what we are experiencing is due to the 26 week development method of Ubuntu. Releases are not delayed because some packages are not fully developed.

Regards

---

### Post by dddman on 2021-05-26
Hello guys

I have both flatpack and snaps installed.  Several of them.  I thought it was a good thing having packages in their own container, but that's a lot of extra weight being added.  I currently use 1/2 of my 20G partition, should of made it bigger.

Synaptic Package Manager I do have installed and I have played with it.  It adds a new way to browse apps, but so complex for just wanting to browse.  It currently sets on the shelf, maybe one day.  I also ran across Aptitude Package Manager and I thought it was nice and it also sets on the shelf.  I guess package managers are not for my browsing pleasure.  However with 50K of packages it needs further exploring.

Graham; I also have the Gnome desktop and the Vanilla Gnome Desktop loaded up.  So who knows where I got it from.  I got in trouble once by mixing too many desktops in one install.  This time I kept it all Gnome.

I'm going to stick with the Ubuntu Gnome Store just because it sounds so official :)

solved by Dennis in post #6

---

### Post by TheFu on 2021-05-26
Actually, having multiple, different, Gnome-based desktops is likely to cause issues. The settings can conflict.
OTOH, having 1 Gnome DE and 1 KDE DE and one no-DE setup (pure WM), shouldn't have any conflicting settings.

The safe answer for having multiple DEs on the same system is to use different usernames for each. Just login under the other userid when you want to use the other DE.  At the system level, the DEs are all stored separately. It is just the per-user config settings that can cause issues.

APT has apt, aptitude, apt-get, synaptic package managers. Each has a place and slightly different capabilities, but they all work with the same backend - APT DB.  For example, aptitude can be smarter about resolving dependency issues. If the install-plan displayed isn't good, we can answer "No", and another install-plan will be displayed.  For end-users, that seldom matters, but for admins where we may use different programs for different services than what Ubuntu considers the default, it can save lots of ugly APT issues.  

For example, about 8 yrs ago, I was using MariaDB well before it became the default DBMS on Ubuntu.  The update for another package had a dependency for mysql ... and was smart enough to know that mariadb and mysql would be a conflict. Unfortunately, the solution decided was to remove mariadb and install mysql.  That broke our project management server and a few others too.  Took me too long and 3 phone calls from really unhappy project managers on a Saturday morning to figure out the problem and correct it.  These days, mariadb is the default and both mariadb and mysql are configured to resolve any dbms dependency, so the exact problem I had won't happen now.  But, things are always changing.  Some package, some where, has the wrong dependencies and it will remove something, then install something else. That, I'm certain about.  LVM snapshots make removing update screw-ups trivial now, provided the system has LVM and the admin makes a snapshot before doing updates.

BTW, 20G was fine pre-18.04.  20.04 minimum storage, thanks to snaps and bloated GUIs is really more like 40G.  My desktop was happy with 20G from 2008 ... until 20.04.  With 20.04, it ran out of space in just a few months and I did some ugly LVM voodoo to add more. See:
```
$ lsblk 
NAME                       SIZE TYPE FSTYPE      MOUNTPOINT
sr0                       1024M rom              
vda                         30G disk             
&#9500;&#9472;vda1                     512M part vfat        /boot/efi
&#9500;&#9472;vda2                       1K part             
&#9492;&#9472;vda5                    29.5G part LVM2_member 
  &#9500;&#9472;**vgubuntu--mate-root**     19G lvm  ext4        /
  &#9500;&#9472;vgubuntu--mate-swap_1  4.1G lvm  swap        [SWAP]
  &#9492;&#9472;vgubuntu--mate-home     12G lvm  ext4        /home
vdb                         10G disk             
&#9492;&#9472;vdb1                      10G part LVM2_member 
  &#9492;&#9472;**vgubuntu--mate-root**     19G lvm  ext4        /

$ sudo pvs
  PV         VG            Fmt  Attr PSize   PFree
  /dev/**vda5**  vgubuntu-mate lvm2 a--  <29.50g    0 
  /dev/**vdb1**  vgubuntu-mate lvm2 a--  <10.00g 4.39g
```
See how my root LV is on 2 different disks?  That's ugly.

---

### Post by Dennis N on 2021-05-26
> However with 50K of packages it needs further exploring.

The 50,000 packages are not all Applications. Many are there as support packages to make user applications work;  I don't think this type of package is listed in Ubuntu Software or Gnome Software.

_A few other comments_:

Ubuntu Software IS a snap application. Gnome Software is not. Being a snap, Ubuntu Software is so far unable to manage Flatpak applications. Gnome Software can manage both Snap packages and Flatpak packages by use of plugins (which are optional). Both Flatpak and Snap can also be managed with terminal commands if necessary.

Flatpaks are built to use particular runtime packages, which provide the common support libraries for a subset of Flatpak applications to function. If several need the same runtime, they share it rather than do a duplicate install of the same runtime. The same is true for Snaps.

Sometimes, the runtime needed by an application changes and you get a new runtime installed to go with it. At least with Flatpak, the old one can be uninstalled if not used by some other application. 
 
Flatpak applications in general seem to me faster than Snaps when opening - hard to distinguish from apt packages. 

Both Snap and Flatpak repositories are usually quickly updated to have the most recent stable application versions available.   

Nowadays, with newer versions of Gnome Software, the Flatpak application updates are automatic and installed in the background, and the Gnome user gets a notification. I also have noticed Snaps are now refreshed by Software Updater after doing other updates.

Yes, you will need more disk space to accommodate your Snap and Flatpak collections.

---

### Post by TheFu on 2021-05-26
I'm 100% positive that snaps will automatically update - whether that is desired or not. No user action needed.

If a GUI app is installed via a snap and has a Qt dependency, then another GUI app is installed via flatpak and has a Qt dependency, then there could be 3 copies (or more) of the Qt libraries on the system.

---

### Post by dddman on 2021-05-26
Creating a user account for a desktop install makes perfect sense, thanks.  I do think my desktop jumping days are over thou, I'm happy with Ubuntu.

And I don't know about expanding a .vdi (vbox) partition.  I have been working on this install for a month, I have my programs in place and lots of tweaks; my storage consumption will slow down but it is still a work in progress.  So maybe I make it for a year or two longer or maybe I can come up with a spooky fix :)  For the moment 20G is good enough.

I think LVM was offered during the Ubuntu install.  I opted out since this is a virtual install.

Thanks for all your detailed input

Dennis N:  Thank you!  That explains a lot.  I do recall having to load the flatpac plugin for the software store to work.  It all makes sense now.

----solved----

---

