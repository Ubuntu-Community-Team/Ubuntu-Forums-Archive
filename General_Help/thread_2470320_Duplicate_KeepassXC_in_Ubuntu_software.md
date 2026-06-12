---
title: "Duplicate KeepassXC in Ubuntu software"
date: 2021-12-25
forum: General Help
---

### Post by cam17 on 2021-12-25
There are 2 identical versions of KeepassXC in the Ubuntu software. They both have the same name and icon but one is an older version. I think they are from the same company accept one has the name of the developer and the other company. This should be corrected and the older version removed as it is missing several key features and has bugs like menu item has the same icon for different functions.

---

### Post by Holger_Gehrke on 2021-12-25
If you look very closely at the details of the two, you'll probably find the new one is a snap and the older one is a 'normal' (.deb) package. Debian packages are kept at the same version for the life of a release (to the point were sometimes bug fixes are backported to the older version instead of putting the newer version in the repositories) except in some very rare special cases (web browsers and the kernel, mainly). That an older version is missing features of a newer version is normal, but the icon problem is probably down to the icons needed for these items not being installed and being quietly substituted with some default icon. If you run it from the command line you'll probably see a ton of warnings about not finding some icon. Try some different icon sets to see whether this changes that behaviour.

Holger

---

### Post by cam17 on 2021-12-26
That still does not make sense. what purpose does it serve to show 2 downloadable versions of a security software which doesn't function the same?

---

### Post by yetimon_64 on 2021-12-27
> **cam17 said:**
> ...what purpose does it serve to show 2 downloadable versions of a security software which doesn't function the same?
If the 2 versions are debian and snap packages, then "choice" of using a debian package for such useful security software like KeepassXC for those Ubuntu users that don't use or don't have snapd installed (some uses even actively remove it for various reasons).

On Xubuntu 20.04 I am happily using the debian package version of KeepassXC, and no bugs have been noted with daily usage here; I find it indispensable. One of the first packages I choose to remove when installing Xubuntu is "snapd" so I'm really glad there is a debian package for KeepassXC.

```
yetiman :~$ apt-cache policy snapd
snapd:
  Installed: (none)
  Candidate: 2.51.1+20.04ubuntu2
  Version table:...
```

Regards, yeti.

---

### Post by cam17 on 2021-12-28
The Ubuntu software installer does not clearly identify the app as debian and I do not understand your response that it worked for you with no problems as the old 2.4.3 version has two menu icons that are identical and perform different versions. There is at least one of 2 serious issues with the older version of the app if a user is confused enough to select the old version 2.4.3 instead of the current 2.6.6 version. Also the updated version says Dec-12-2021 for both see enclosed

---

### Post by TheFu on 2021-12-28
> **cam17 said:**
> That still does not make sense. what purpose does it serve to show 2 downloadable versions of a security software which doesn't function the same?

Choice is a cornerstone for all Linux systems.
Because some of us would rather run the older version that isn't a snap package. 
Perhaps the person who created the snap package isn't an official member of the KeePassXC team?
Perhaps the KeePassXC team hasn't formally decided to support snaps?
Anyone can create a snap for any package.  In the very early days of snaps, there were a number of unofficial, snap, packages NOT created by the actual team that was behind the software included in the snap.

Feel free to ignore the version you don't want.  That's your choice.

---

### Post by yetimon_64 on 2021-12-28
> **cam17 said:**
> ...There is at least one of 2 serious issues with the older version of the app if a user is confused enough to select the old version 2.4.3 instead of the current 2.6.6 version...
No confusion here, just exercising my choice to not use a snap package. The fact is I don't use the software centre at all on Xubuntu so I don't even see the newer version...
```
apt-cache policy keepassxc
keepassxc:
  Installed: 2.4.3+dfsg.1-1build1
  Candidate: 2.4.3+dfsg.1-1build1
  Version table:
 *** 2.4.3+dfsg.1-1build1 500
        500 http://archive.ubuntu.com/ubuntu focal/universe amd64 Packages
        100 /var/lib/dpkg/status
```
_**If**_ removing the 2.4.3 version of keepassxc from the software centre involves removing it from the repositories, then I'd end up having to compile from source and manually update etc.

As for the "issues" you mention that I am not seeing here... Can you supply a link to a launchpad bug report so I can better understand your complaints on the older version? I really don't know what menu items/icons are "duplicated" except for the stock/default key icon on title entries in a database ... See first attachment.

For an example of the title entries with custom icons set ... see second attachment.
> ...and has bugs like menu item has the same icon for different functions. 
I cannot see any example within keepassxc where there are "duplicate" menu items except the key icon in a database. This is not a bug if it is what you are referring to, it is a "default" icon; the user has to either choose an icon from the default set from the icon tab within an entry or can supply a custom icon and set it within the icon tab ... see third attachment for where I go to set custom icons on a database entry (this example is currently set as the default icon, the "custom" option is at the bottom of the screenshot).

It would be easier to help you if you could link to a bug report for the issues you are having or even explain more fully as to what you think is a bug in the older version. Removing the older version would severely impact many users.

>  Feel free to ignore the version you don't want.  That's your choice.                 
+1

Regards, yeti.

---

