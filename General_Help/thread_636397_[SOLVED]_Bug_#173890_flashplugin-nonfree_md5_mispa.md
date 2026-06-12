---
title: "[SOLVED] Bug #173890 flashplugin-nonfree md5 mispatch support thread"
date: 2007-12-09
forum: General Help
---

### Post by daradib on 2007-12-09
This fix has bugs when used with Konqueror and Opera (see Apparent Problems with These Fixes).

[CENTER][B][SIZE="3"]
This problem has been officially fixed. See Official Fix (in blue) for more information

The fix provided here is no longer relevant and no longer works due to Adobe's update.

Please use the flashplugin-nonfree package included in Ubuntu.
[/SIZE][/B][/CENTER]

This is the support thread for **[Launchpad Bug# 173890]("https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890").** Posts non-developer related should be put in this thread, rather than in the [bug]("https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890") comments to prevent Ubuntu developers from being [flooded by unnecessary information]("https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890/comments/28").

**Bug Symptoms**

The flashplugin-nonfree package fails to install with the following error (viewable only in detailed or verbose mode):
```

md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
```

**Note: If you install the Adobe flash player plugin without viewing the detailed terminal text, the package will appear to be installed, but Flash will not work in Firefox** ([Launchpad Bug# 175255]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/175255")). If one gets repeated messages in Firefox about installing the Adobe Flash Plugin, then this bug is at fault. There is [Lauchpad Bug #175255]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/175255") for the apparent successful installation of a package when the md5sums fail.

This is a very recent bug, caused by [Adobe's update of Flash 9.0 update 3]("http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html") (9.0.115.0) codename "Moviestar" on December 4th.

The change causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). This bug has been [fixed in the next release of Ubuntu (Hardy 8.04)]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2") and it should [soon come as an update to Ubuntu 7.10]("https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890/comments/21").

[COLOR="Blue"]**Official Fix**

> *** IMPORTANT NOTICE ***
The fix for this plugin has been released (let's hope that it will last and adobe won't change the md5sum again)
From the menu:
System -> Administration -> Software sources -> be sure than you have selected the "main", "universe", "restricted" and multiverse".
Then go to the Updates tab -> check "security", "updates" and "proposed"
Now "Close" and "Reload".

after that, do this in the terminal:
sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

*** IMPORTANT NOTICE no.2 ***
For all of you that *STILL* complain, which repositories do you use?
Check if your repositories are up to date: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)
Otherwise, try switching to "Download from" -> "Main server" (at system -> administration -> software sources)
Close and Reload.

Then do this in terminal:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get remove -y --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

If the above don't work, please post your Ubuntu version release and apt-cache policy flashplugin-nonfree info, it will be easier to track down.[/COLOR]

**Main Fix**

The fix for this bug has been uploaded to all proposed Ubuntu repositories. Please see [this]("https://www.launchpad.net/ubuntu/+source/flashplugin-nonfree/"). This is for all Ubuntu releases from 6.06 through 7.10. This means the fix should be available very soon through the repositories (the binary packages have been built) if the proposed repository is enabled. Of course, this is still susceptible to the same problems as this fix (including no flash plugin support in Konqueror).

[B]Remember to completely remove gnash before installing flashplugin-nonfree.
[/B]
To enable the proposed repository, go to System -> Administration -> Software Sources. Under the Updates tab, check pre-released updates. When you close the window, it will then say package information is out of date, so click Reload. You may need to uninstall the package obtained through the immediate fix to download the package through the repositories.
[I]
Currently unnecessary:[/I] Ubuntu 7.10 releases have been built by me and I have attached a mirror of the other releases when they were hosted by the Ubuntu repository (not anymore).

**32-bit packages:** The Ubuntu 7.10 package is available [here]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466"). Just download the package for your release, double-click the file, and install the package. For other releases, download and extract [this archive]("http://ubuntuforums.org/attachment.php?attachmentid=57896") and double-click the corresponding file to your release.

**64-bit packages:** The Ubuntu 7.10 package is available [here]("http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466"). Just download the package for your release, double-click the file, and install the package. For other releases, download and extract [this archive]("http://ubuntuforums.org/attachment.php?attachmentid=57896") and double-click the corresponding file to your release. However, I do not believe you will be able to use 64-bit flashplugin-nonfree packages without modifications on Ubuntu releases before 7.10.

```
Ubuntu 6.06 32-bit: flashplugin-nonfree_9.0.115.0ubuntu0.6.06_i386.deb
Ubuntu 6.06 64-bit: flashplugin-nonfree_9.0.115.0ubuntu0.6.06_amd64.deb
Ubuntu 6.10 32-bit: flashplugin-nonfree_9.0.115.0ubuntu0.6.10_i386.deb
Ubuntu 6.10 64-bit: flashplugin-nonfree_9.0.115.0ubuntu0.6.10_amd64.deb
Ubuntu 7.04 32-bit: flashplugin-nonfree_9.0.115.0ubuntu0.7.04_i386.deb
Ubuntu 7.04 64-bit: flashplugin-nonfree_9.0.115.0ubuntu0.7.04_amd64.deb
Ubuntu 7.10 32-bit: flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb
Ubuntu 7.10 64-bit: flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.deb
Ubuntu 8.04 32-bit (development-Hardy): flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb
Ubuntu 8.04 64-bit (development-Hardy): flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb
```

**Apparent Problems with These Fixes**

These problems are relevant to all of the supplied fixes. That is because all of these fixes are almost identical to each other, all employing Flash 9 Update 3. The fixes are only different packages or sometime just different locations from the same package.

The new version of Flash is incompatible with Konqueror because it requires XEmbed ([Launchpad Bug# 174343]("https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/174343")). 9.0.48.0 is the last version of flash to support Konqueror in its current state.

The new version of Flash is only compatible with 9.50 Beta 2 of Opera (and later).

Some sites, including disney.com and nick.com do not load properly. It would be great if someone tests these sites with an older flash plugin and with Windows Flash Update 3. This only appears to affect 64-bit SMP/SMT machines (i.e. multicore, multiprocessor, including presumably Intel HyperThreading). See Fixes for Further Problems for a solution.

On Launchpad Bug Comments, by [selivanow]("https://www.launchpad.net/~selivanow/")
> Adobe updated the flash plugin. Due to their license, we must download and install their file. This breaks the Gutsy package. We have TWO choices:

1) Don't update the package and have a broken package that no-one can use (aside from the more technically minded)

2) Update the package and have a package that everyone can use, except for konqueror users.

It seems that because we have no control over Adobe, the ball is in konqueror's court and they need to patch. (If their users plan on using flash)

A third solution, if possible, would be to see if Adobe keeps older versions of flash available for download and update the package to pull that.

Indeed, Adobe does keep older version of Flash available for download. However, it is not feasible for end users. The only way is through [this archive of flash 9 releases]("http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip") (over 65 MB in size), including installers for all supported platforms).

**How to Avoid This Problem Again**

If no action is taken, incidents like these will occur every time a new flashplugin is released. Therefore, and as a result of [Saïvann Carignan's]("https://www.launchpad.net/~saivann") [bug comment]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/175255/comments/13") on [Launchpad Bug 175255]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/175255"), I recommend everyone to contact Adobe as specified in the below quote so that incidents like these will not happen again (i.e. permanent location of flash plugin releases, keep older versions of flash as separate downloads, and/or permission to redistribute the flashplugin binary within Ubuntu).

> I contacted Adobe and they suggest that linux users ask for this [avoid updating the flash plugin without renameing the file (to reflect the version)] at [www.adobe.com/go/wish](www.adobe.com/go/wish)
To every ubuntu users that does not want flashplugin-nonfree to get into problems at each update of flash from adobe, I suggest to ask Adobe to provide permanent links for all recent linux version of flash.

**Fixes for Further Problems**

This release of flash is generally less stable in comparison with the older release (9,0.48.0). However, there is a specific issue which exists and fortunately can be fixed that only apparently affects 64-bit SMP/SMT machines (i.e. multicore, multiprocessor, including presumably Intel HyperThreading).

The flashplugin can crash on certain websites, causing a white or grey area to be displayed where the flash content should exist. The web browser must be restarted to use the flashplugin again.

The bug that causes the crash is [Launchpad Bug# 177856]("https://bugs.launchpad.net/nspluginwrapper/+bug/177856") and it only affects 64-bit systems, which rely on nspluginwrapper to run the 32-bit flash plugin.

The nspluginwrapper author has provided a patch: [http://launchpadlibrarian.net/11055616/npw.gthreads.diff](http://launchpadlibrarian.net/11055616/npw.gthreads.diff)

And [Rashad Tatum]("https://bugs.launchpad.net/~rmtatum") built a fixed package: [http://launchpadlibrarian.net/11224902/nspluginwrapper_0.9.91.5-1ubuntu2_amd64.deb](http://launchpadlibrarian.net/11224902/nspluginwrapper_0.9.91.5-1ubuntu2_amd64.deb)

Thanks [Riccardo Pellegrini]("https://bugs.launchpad.net/~cionci") and nspluginwrapper author.

**Why the packages have been removed from the proposed repository**

Updated packages have been now added to the proposed repository, so this information is presently irrelevant, and exists for historical reasons.

[Bug Comment]("https://bugs.launchpad.net/ubuntu/dapper/+source/flashplugin-nonfree/+bug/173890/comments/73"):
> 
ok , I'm reopening this task as the fix in -proposed was not good for all and has been removed from the archive ( e.g. FF and Konq and Opera ) I have another fix in the works that will be uploaded to -proposed shortly ( before Wednesday hopefully but dont hold me to this )

Please dont add any more "works for me" or "dosent work for me" comments to this bug for now, untill I upload a new version to proposed.

see this Ubuntu-Devel post for more details on the exact situation and possible solutions ( Development wise, not end user solutions )

[https://lists.ubuntu.com/archives/ubuntu-devel/2007-December/024877.html](https://lists.ubuntu.com/archives/ubuntu-devel/2007-December/024877.html)

[B]
Archived Instructions[/B]
> 
**Immediate Fix (New)**

*These instructions are now outdated, as Launchpad has built 32-bit and 64-bit packages. Please use the main fix (above).*

[QUOTE]These instructions use the currently existing source packages in the official Ubuntu proposed repository and compile them to create installable binary packages. Please check the official fix first and use the binary package if it is available. Otherwise, use these instructions.

You may use a binary package I built, or build it yourself following the method I used (the packages you create will be identical to mine). It is therefore optional and unnecessary to build your package as I have provided binary packages, but instructions are in this post here if you wish to do so.

Using Synaptic Package Manager, completely remove (right-click the package, "Mark for Complete Removal") the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): ```
sudo apt-get remove --purge flashplugin-nonfree
```

For **32-bit Ubuntu**: Please see Official Fix above.

For **64-bit Ubuntu 7.10**: Just download [REMOVED] this package (attachment to this post), double-click the file, and install the package. You can always wait for the update through an official repository. A 64-bit flashplugin-nonfree package is only available for Ubuntu 7.10 and newer.

For **64-bit Ubuntu 8.04**: Just download [REMOVED] this package (attachment to this post), double-click the file, and install the package. You can always wait for the update through an official repository.

**Immediate Fix (Old)**
[I]
These instructions are now outdated, as release-specific packages have been released. Please use the main fix (above).[/I]

> Using Synaptic Package Manager, completely remove (right-click the package, "Mark for Complete Removal") the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): ```
sudo apt-get remove --purge flashplugin-nonfree
```

For **32-bit Ubuntu**: Just download [this package]("http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb") (requires Launchpad account) or the [REMOVED] attachment to this post (they are identical to the current package in the next release of Ubuntu, Hardy 8.04), double-click the file, and install the package. You can always wait for the update through an official repository.

For **64-bit Ubuntu 7.10 only**: You should be aware that an "official" package has not been built. However, I built [this package]("http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb") from the "official" source package uploaded to the Hardy repositories by [Brandon Holtsclaw]("https://www.launchpad.net/~imbrandon/"). This package should be identical to the "official" package that will be created, but you can always wait for the update through an official repository.

**Build Package from Source (optional)**

*These instructions are now outdated, as Launchpad has built 32-bit and 64-bit packages. Please use the main fix (above).*

> **New Fix**

These instructions are for Ubuntu 7.10. Make the necessary minor adjustments for older releases (32-bit only). Do not use these packages on 64-bit Ubuntu releases older then Ubuntu 7.10.

The Ubuntu proposed repository and source code must be enabled. To enable the proposed repository, go to System -> Administration -> Software Sources. Under the Updates tab, check pre-released updates. Under the Ubuntu Software tab, check Source code. When you close the window, it will then say package information is out of date, so click Reload.

You can build your own package from source using the following terminal instructions (Applications -> Accessories -> Terminal).
```
sudo apt-get install build-essential fakeroot
sudo apt-get build-dep flashplugin-nonfree
apt-get source flashplugin-nonfree
cd flashplugin-nonfree-9.0.115.0ubuntu0.7.10
dpkg-buildpackage -b -rfakeroot
```

The first line and second lines download and install all of the dependencies for the flash plugin (including development dependencies). The third line downloads the source package. The fourth line changes into the directory created by the extracted file. The fifth line builds a binary package.

Now if you go to Places -> Home you should see a file named flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.deb or flashplugin-nonfree_9.0.115.0ubuntu0.7.10.deb (depending on your architecture). Double-click the file and install the package.

It is perfectly normal to get the following warning and messages while compiling:
```
dh_builddeb -pflashplugin-nonfree
warning, `debian/flashplugin-nonfree/DEBIAN/control' contains user-defined field `Npp-Applications'
warning, `debian/flashplugin-nonfree/DEBIAN/control' contains user-defined field `Npp-Mimetype'
warning, `debian/flashplugin-nonfree/DEBIAN/control' contains user-defined field `Npp-Name'
warning, `debian/flashplugin-nonfree/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `flashplugin-nonfree' in `../flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.deb'.
dpkg-deb: ignoring 4 warnings about the control file(s)
 dpkg-genchanges -b
dpkg-genchanges: warning: unknown information field 'Xb-Npp-Mimetype' in input data in package's section of control info file
dpkg-genchanges: warning: unknown information field 'Xb-Npp-Applications' in input data in package's section of control info file
dpkg-genchanges: warning: unknown information field 'Xb-Npp-Name' in input data in package's section of control info file
dpkg-genchanges: binary-only upload - not including any source code
 signfile flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.changes
gpg: skipped "Brandon Holtsclaw <imbrandon@kubuntu.org>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

dpkg-buildpackage: binary only upload (no source included)
(WARNING: Failed to sign .changes file)
```

Just install the binary package you generated (probably in your home directory). You can ignore the warnings. And you don't want a source package (only a binary for installation). You also don't need any GPG keys, as you don't need to verify that Brandon's package is his and sign the package. Everyone will have exactly the same message as you if they do the same instructions (and assuming they haven't added Brandon's GPG keys- which is pointless for building a binary package).

**Old Fix**

Alternatively, you can build your own package from source using the following terminal instructions (Applications -> Accessories -> Terminal).
```
sudo apt-get install build-essential fakeroot
sudo apt-get build-dep flashplugin-nonfree
wget http://launchpadlibrarian.net/10756602/flashplugin-nonfree_9.0.115.0ubuntu2.tar.gz
tar -zxvf flashplugin-nonfree_9.0.115.0ubuntu2.tar.gz
cd flashplugin-nonfree-9.0.115.0ubuntu2
dpkg-buildpackage -b -rfakeroot
```

The first line and second lines download and install all of the dependencies for the flash plugin (including development dependencies). The third line downloads the tar.gz file. The fourth line extracts the downloaded file. The fifth line changes into the directory created by the extracted file. The sixth line builds a binary package.

Now if you go to Places -> Home you should see a file named flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb or flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb (depending on your architecture). Double-click the file and install the package.

It is perfectly normal to get the following warning and messages while compiling:
```
dh_builddeb -pflashplugin-nonfree
warning, `debian/flashplugin-nonfree/DEBIAN/control' contains user-defined field `Npp-Applications'
warning, `debian/flashplugin-nonfree/DEBIAN/control' contains user-defined field `Npp-Mimetype'
warning, `debian/flashplugin-nonfree/DEBIAN/control' contains user-defined field `Npp-Name'
warning, `debian/flashplugin-nonfree/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `flashplugin-nonfree' in `../flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb'.
dpkg-deb: ignoring 4 warnings about the control file(s)
 dpkg-genchanges -b
dpkg-genchanges: warning: unknown information field 'Xb-Npp-Mimetype' in input data in package's section of control info file
dpkg-genchanges: warning: unknown information field 'Xb-Npp-Applications' in input data in package's section of control info file
dpkg-genchanges: warning: unknown information field 'Xb-Npp-Name' in input data in package's section of control info file
dpkg-genchanges: binary-only upload - not including any source code
 signfile flashplugin-nonfree_9.0.115.0ubuntu2_amd64.changes
gpg: skipped "Brandon Holtsclaw <imbrandon@kubuntu.org>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

dpkg-buildpackage: binary only upload (no source included)
(WARNING: Failed to sign .changes file)
```

Just install the binary package you generated (probably in your home directory). You can ignore the warnings. And you don't want a source package (only a binary for installation). You also don't need any GPG keys, as you don't need to verify that Brandon's package is his and sign the package. Everyone will have exactly the same message as you if they do the same instructions (and assuming they haven't added Brandon's GPG keys- which is pointless for building a binary package).[/QUOTE]

By the way, I am [Cyrus Jones]("https://www.launchpad.net/~daradib") on Launchpad.

---

### Post by JanC on 2007-12-09
Thanks for moving this here!  :-)

I'm not an Ubuntu developer myself, but I give support (among other things) in the Dutch-speaking community & contacted the developers about this bug after someone on IRC asked questions about this problem.

Please also keep in mind that building your own packages is not the best solutions for most users (because it's way too complicated for them).  That's why I reminded that people could wait for official packages.  It's always good to explain this for less-experienced users (this is Ubuntu after all, not Gentoo or Slackware).

---

### Post by daradib on 2007-12-09
> **JanC said:**
> Please also keep in mind that building your own packages is not the best solutions for most users (because it's way too complicated for them).  That's why I reminded that people could wait for official packages.  It's always good to explain this for less-experienced users (this is Ubuntu after all, not Gentoo or Slackware).

Agreed.

---

### Post by buntunub on 2007-12-10
This does not work for me. Neither your prebuilt package nor your build instructions. Here are the errors resulting for the buildpackage:

 dpkg-buildpackage -b -rfakeroot
dpkg-buildpackage: source package is flashplugin-nonfree
dpkg-buildpackage: source version is 9.0.115.0ubuntu2
dpkg-buildpackage: source changed by Brandon Holtsclaw <imbrandon@kubuntu.org>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 9.0.115.0ubuntu2
 fakeroot debian/rules clean
/usr/bin/dpkg-buildpackage: 224: fakeroot: not found

Any ideas?

---

### Post by buntunub on 2007-12-10
Ok I installed fakeroot and built the package lol. However, that simply builds the package that you already did, which does not work properly. It only works on youtube, but wont load other flash sites like disney.com or nick.com. Any ideas?

---

### Post by kitomokito on 2007-12-10
This solved my problem. Thanks a lot daradib :)

---

### Post by firephoto on 2007-12-10
Updating things to pull in the latest flash plugin won't work for kubuntu and konqueror because the newer flash plugin is incompatible so i'm not sure how the 'soon to be released" update will work...

Is there a reason why the original package wasn't updated to download the correct version of flash?

---

### Post by daradib on 2007-12-10
> **buntunub said:**
> Ok I installed fakeroot and built the package lol. However, that simply builds the package that you already did, which does not work properly. It only works on youtube, but wont load other flash sites like disney.com or nick.com. Any ideas?

I don't know. I realized I have the same problem, but I never used those sites before. What is interesting, however, is that the page loads (I see animations) and then is covered by a dark blue screen.

---

### Post by daradib on 2007-12-10
It would be good if someone tests Windows with the new flash player. Do disney.com and nick.com work?

---

### Post by daradib on 2007-12-10
> **firephoto said:**
> Is there a reason why the original package wasn't updated to download the correct version of flash?

Well there does not seem to be any easy way to download old flash plugin from Adobe's website.

The only way is through the following archive of older flash 9 releases (over 65 MB in size)

[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip)

And maybe Macromedia does not permit redistribution of the flash player so it might not be legally possible to only host 9.0.48.0 somewhere else. You should check their license (EULA).

---

### Post by buntunub on 2007-12-11
> **daradib said:**
> I don't know. I realized I have the same problem, but I never used those sites before. What is interesting, however, is that the page loads (I see animations) and then is covered by a dark blue screen.

Ya. You can tell that it actually loads up and then just dissapears. Nick.com only loads a few things but leaves the rest the page blank.

---

### Post by daradib on 2007-12-11
This is a problem for Opera (as well as Konqueror) in Ubuntu. 9.50 Beta 2 of Opera (and later) are the only versions of Opera that can handle the new plugin.

On Launchpad Bug Comments, by [selivanow]("https://www.launchpad.net/~selivanow/")
> Adobe updated the flash plugin. Due to their license, we must
download and install their file.
This breaks the Gutsy package.
We have TWO choices:

1) Don't update the package and have a broken package that no-one can
use (aside from the more technically minded)
2) Update the package and have a package that everyone can use, except
for konqueror users.

It seems that because we have no control over Adobe, the ball is in
konqueror's court and they need to patch. (If their users plan on
using flash)

A third solution, if possible, would be to see if Adobe keeps older
versions of flash available for download and update the package to
pull that.

-Chris

---

### Post by muncrief on 2007-12-12
Currently neither the flashplugin-nonfree or IcedTea or Blackdown Java plugins work in Firefox 64, and reportedly Konqueror or Opera (I don't run them so I don't know), on Gusty AMD64. However I've found two workarounds that work very well for me. I'm running Ubuntu Gutsy AMD64 on an nForce4 based platform with an Athlon64 X2 4200+ at 2.65GHz, 3GB DDR, and an Nvidia 7800GT video card. Here's what I've done:


Flash
------
> Close all web browsers!

Open a terminal
cd
rm .mozilla/firefox/pluginreg.dat
sudo aptitude remove flashplugin-nonfree
sudo aptitude install ia32-libs ia32-libs-gtk lib32asound2
sudo aptitude install nspluginwrapper gsfonts-x11

**For Older Flash Player** (which seems more compatible with more sites for the moment)

(**Important Note:** you need to take out the space in "i nstallers" below, there's a bug in this editor that's inserting a space and I can't stop it)
wget http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip
unzip fp9_archive.zip
tar -xzvf fp9_archive/9r48/install_flash_player_9r48_linux.tar.gz
sudo cp install_flash_player_9_linux/libflashplayer.so /usr/lib/mozilla/plugins
sudo cp install_flash_player_9_linux/flashplayer.xpt /usr/lib/mozilla/plugins
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

**For Newest Flash Player** (doesn't work on disney.com, nick.com, and reportedly Konqueror):

(**Important Note:** you need to take out the space in "c urrent" below, there's a bug in this editor that's inserting a space and I can't stop it)
wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
tar -xzvf install_flash_player_9_linux.tar.gz
sudo cp install_flash_player_9_linux/libflashplayer.so /usr/lib/mozilla/plugins
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so


And that's it!. One caveat whether you have the official Ubuntu package or install the way I've described is that every once in awhile flash will stop working. This usually occurs after a Firefox or plugin upgrade of some type, but can occur for seemingly no reason. If this does happen, just execute the following commands to restore flash functionality:

> Close all web browsers!

Open a terminal
cd
rm .mozilla/firefox/pluginreg.dat
sudo nspluginwrapper -u /usr/lib/mozilla/plugins/npwrapper.libflashplayer.so


Sun Java 7 beta (IcedTea Java)
---------------------------------------

To get a working Java Firefox plugin you unfortunately have to compile Java from the source. Now don't worry, it's really very easy, it just takes a long, long, long, time. The night I compiled it I waited for three hours, and finally went to bed. However when I woke up the next morning it was done and Java 7 worked beautifully, including the Firefox browser plugin!

Now what's odd here is that the package version we're going to build is in the Ubuntu repositories, but for some reason Java won't work unless it's actually compiled on your machine. So here we go:

> Close all web browsers!

Open a terminal
cd
sudo apt-get build-dep icedtea-java7-plugin
sudo apt-get -b source icedtea-java7-plugin icedtea-java7-bin icedtea-java7-jre icedtea-java7-jdk
sudo dpkg -i icedtea-java7-*deb


And that's it. However as I said, it takes a very long time to compile even on a fairly speedy dual core machine, and it's the "sudo apt-get -b" command that takes so many hours. So just be patient, and you will have Java.

The update icon might also pop up asking you to upgrade Java after installation, but you will notice that both versions are the same. DO NOT UPGRADE. Java will still work, but there will be a lot of jerking and other anomalies if you do. Instead, go into package manager, select all the icedtea-java packages, and then go to the menu bar and click "Package->Lock Version". This will not stop the update icon from appearing, but it will stop Java from being overwritten during other upgrades. Of course, when the update version changes you should unlock the packages and try the new version.

One other word of warning, do not substitute "aptitude" for "apt-get" in the Java build commands. They are special package commands that aptitude does not implement.

I hope this helps until the problems with these packages are worked out.

---

### Post by TheShocker on 2007-12-12
Thanks to the OP for posting this. I try to install your package but I get an error saying I don't have permission to access it.

I have uninstalled flash for the moment. I think I will wait for an official fix. How long does this usually take? I am new to Ubuntu.

---

### Post by DasCrushinator on 2007-12-12
Is there any official word on when this will be fixed in the repos?

---

### Post by daradib on 2007-12-12
> **TheShocker said:**
> Thanks to the OP for posting this. I try to install your package but I get an error saying I don't have permission to access it.

I have uninstalled flash for the moment. I think I will wait for an official fix. How long does this usually take? I am new to Ubuntu.

You need to be logged into [Launchpad]("https://www.launchpad.net/ubuntu") to download the file. If you have not done so already, you should really register with Launchpad, as it is very useful and an important account that can be used for Launchpad itself as well as the Ubuntu Wiki / Community Documentation. However, I will attach the file to my post so it can be downloaded from Ubuntu Forums directly, as long as you have an Ubuntu Forums account (which obviously you do).

You should read the [Launchpad bug]("https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890") comments if you want to understand when this bug will be fixed. I am trying to get this new package uploaded to the Ubuntu 7.10 repositories (it is already in Ubuntu 8.04 Hardy repositories). Unfortunately, there are certain problems with this new flash plugin (See my first post in this thread- Apparent Problems with this Fix). In does not help that Adobe's license prohibits distribution of the flash player (it must be downloaded from Adobe's website- the Ubuntu packages do this and a few other things including nspluginwrapper to allow the plugion to be used on 64-bit Firefox) since there is no feasible method for users to get the old flash plugin (without downloading over 65 MB).

---

### Post by daradib on 2007-12-12
> **muncrief said:**
> Currently neither the flashplugin-nonfree or IcedTea or Blackdown Java plugins work in Firefox 64, and reportedly Konqueror or Opera (I don't run them so I don't know), on Gusty AMD64. However I've found two workarounds that work very well for me. I'm running Ubuntu Gutsy AMD64 on an nForce4 based platform with an Athlon64 X2 4200+ at 2.65GHz, 3GB DDR, and an Nvidia 7800GT video card. Here's what I've done:

Flash
------

And that's it!. One caveat whether you have the official Ubuntu package or install the way I've described is that every once in awhile flash will stop working. This usually occurs after a Firefox or plugin upgrade of some type, but can occur for seemingly no reason. If this does happen, just execute the following commands to restore flash functionality:.

Those instructions do work, but it is recommended to use the updated packages (see the first post of this thread) since those will keep package management intact.

---

### Post by daradib on 2007-12-12
[SIZE="4"]**The fix for this bug has been uploaded to all proposed Ubuntu repositories**
[/SIZE]

Please see [this]("https://www.launchpad.net/ubuntu/+source/flashplugin-nonfree/"). This is for all Ubuntu releases from 6.06 though 7.10. This means the fix should be available very soon through the repositories (the binary packages must be built) if the proposed repository is enabled. Of course, this is still susceptible to the same problems as this fix (including no flash plugin support in Konqueror).

To enable the proposed repository, go to System -> Administration -> Software Sources. Under the Updates tab, check pre-released updates. It will then say package information is out of date, so click Reload.

---

### Post by TheShocker on 2007-12-12
Oh that's awesome. I did what you said to do in the Software Sources. The window just closes after updating the package info. I assume once the binary packages are built there will be a notification?

*edit: yep, that's exactly what happened. However, flashplugin-nonfree is not on the list. Maybe I still have to wait for those binaries?

#edit2: Gutsy 64 bit

---

### Post by daradib on 2007-12-12
> **TheShocker said:**
> Oh that's awesome. I did what you said to do in the Software Sources. The window just closes after updating the package info. I assume once the binary packages are built there will be a notification?

*edit: yep, that's exactly what happened. However, flashplugin-nonfree is not on the list. Maybe I still have to wait for those binaries?

Yes, you still have to wait (it would be good though if you specified Ubuntu release and architecture- 32/64 bit)

See [https://www.launchpad.net/ubuntu/+source/flashplugin-nonfree/](https://www.launchpad.net/ubuntu/+source/flashplugin-nonfree/)

Assuming you are running Ubuntu 7.10, you would go here:[https://www.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/9.0.115.0ubuntu0.7.10](https://www.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/9.0.115.0ubuntu0.7.10)

Right now
> Builds

    * gutsy lpia Successfully built (DONE)
    * gutsy i386 Needs building
    * gutsy amd64 Needs building

FYI, lpia is a low power Intel architecture (I think for embedded/small devices)

---

### Post by daradib on 2007-12-12
Well you could install the package under immediate fix new for 64-bit Ubuntu 7.10. I built the source package that is provided on the proposed repository (the binaries still have not built by Launchpad, though the low power architecture has been built- 32-bit will be built next and finally 64-bit).

---

### Post by deeZee on 2007-12-14
> **daradib said:**
> [SIZE="4"]**The fix for this bug has been uploaded to all proposed Ubuntu repositories**
[/SIZE]

Please see [this]("https://www.launchpad.net/ubuntu/+source/flashplugin-nonfree/"). This is for all Ubuntu releases from 6.06 though 7.10. This means the fix should be available very soon through the repositories (the binary packages must be built) if the proposed repository is enabled. Of course, this is still susceptible to the same problems as this fix (including no flash plugin support in Konqueror).

To enable the proposed repository, go to System -> Administration -> Software Sources. Under the Updates tab, check pre-released updates. It will then say package information is out of date, so click Reload.

That worked great for me...thanks!

---

### Post by aliencam on 2007-12-14
I am using Gutsy 64 bit. 

I am still not getting this to work, I have tried using daradib's package that is attached to his post, and it works to load one flash element (and i forgot to install adblock before: brand new computer today)  and after it loads one, it stops working.   so I have to do apt-get remove --purge, then reinstall the deb attachd to the post, then I am able to load only ONE flash item, and no flash works anymore...

I have also tried to see if the one in the repositories is working, and I still get the md5 error.  (i have done apt-get update first)

---

### Post by TheShocker on 2007-12-14
I'm not trying to be critical...but why does it take so long for these to be built? I'm just curious as to how the process works.

---

### Post by mocha on 2007-12-15
I just want to share a few thoughts on this issue, hopefully it will help someone that experiences the same issues as I.

I setup Firefox to use the v115 of the Flash plugin.  This is stable and working a little better than the previous v48 version.

The latest stable of Opera v9.24 doesn't work with v115 of the Flash plugin.  So, I moved all my plugins for Opera to /usr/lib/Opera/plugins/ and in there I put the v48 of the Flash plugin.

So Opera can use v48 and Firefox can use v115 and my system is happy.

Some other things to consider:  The beta versions of Opera v9.50b do work with the v115 of the Flash plugin.  However, this doesn't come without a price, namely that Java apps crash all the time.  That is a major deal breaker for me.  Also, I experienced a hard system freeze last night by keeping Opera v9.50b open on a Flash webpage (YouTube) with v115 in use.  I reported this to the Opera forum and they suggested I try an earlier build, however due to the Java crash problems I decided to go back to the stable v9.24.

---

### Post by aliencam on 2007-12-15
how can you set up firefox to use the old version?? I only just installed ubuntu yesterday, so I can' t just lock the update and keep it working as it did with the old version... all I can think of is to follow muncrief's instructions, but those seem like I wouldn't be able to uninstall the old version to update to a newer one... (without recompiling a newer version when it is released) 

if i'll be able to use package manager or apt-get without conflict when a newer version comes out, i'll install the old version from adobe's giant archive.. 

would the package manager be able to override a previous installation without conflict?

---

### Post by mocha on 2007-12-15
I should've been clearer.  I first saved the v48 files (flashplayer.xpt and libflashplayer.so).  Then I installed v115 with the package manager.  Then I setup the Opera preferences to only look in particular directories for plugins, and I copied the v48 files to that directory.

---

### Post by SilverWave on 2007-12-15
> **daradib said:**
> [SIZE="4"]**The fix for this bug has been uploaded to all supported proposed Ubuntu repositories**[/SIZE]

See the section Official Fix

For **64-bit Ubuntu 7.10 only**: You should be aware that an "official" package has not been built. However, I built [this package]("http://launchpadlibrarian.net/10804892/flashplugin-nonfree_9.0.115.0ubuntu2_amd64.deb") from the "official" source package uploaded to the Hardy repositories by [Brandon Holtsclaw]("https://www.launchpad.net/~imbrandon/"). This package should be identical to the "official" package that will be created, but you can always wait for the update through an official repository.

...

By the way, I am [Cyrus Jones]("https://www.launchpad.net/~daradib") on Launchpad.

Thanks mate I broke my existing working flash setup as I got greedy and wanted full screen to work on the new BBC iplayer service :(

The 64bit deb works like a treat all working ok - Thanks!

You may get a lot of hits because of the iplayer ;)
[http://www.bbc.co.uk/iplayer/](http://www.bbc.co.uk/iplayer/) beta...



:D

---

### Post by berlinbrown on 2007-12-15
Does this work with Firefox beta 3 (which I downloaded from the mozilla firefox site)?  Eg., not firefox2.

I hate firefox2

---

### Post by daradib on 2007-12-15
> **berlinbrown said:**
> Does this work with Firefox beta 3 (which I downloaded from the mozilla firefox site)?  Eg., not firefox2.

I hate firefox2

I assume you mean Firefox 3 Beta 1 (not to be picky, but Firefox Beta 3 would be the third beta). It should work, as this package has nothing to do specifically with Firefox 2.

FYI I use Swiftweasel instead of Firefox and flash is fine.

---

### Post by daradib on 2007-12-15
> **aliencam said:**
> I am using Gutsy 64 bit. 

I am still not getting this to work, I have tried using daradib's package that is attached to his post, and it works to load one flash element (and i forgot to install adblock before: brand new computer today)  and after it loads one, it stops working.   so I have to do apt-get remove --purge, then reinstall the deb attachd to the post, then I am able to load only ONE flash item, and no flash works anymore...

I have also tried to see if the one in the repositories is working, and I still get the md5 error.  (i have done apt-get update first)

May I ask what browser you are using. Are you using Firefox? Try starting firefox from terminal and recording any messages.

---

### Post by daradib on 2007-12-15
> **TheShocker said:**
> I'm not trying to be critical...but why does it take so long for these to be built? I'm just curious as to how the process works.

Launchpad autobuilds binary packages from source packages which are included in the repositories. However, I have seen that 64-bit binary builds of at least the package flashplugin-nonfree (if not other packages) have either stalled or become really slow. After 10 days, the new flashplugin-nonfree package in hardy has still not started building for 64-bit (although the 32-bit build was done the next day after the source package was uploaded).

Now, you can look at [Launchpad's build farm]("https://www.launchpad.net/+builds/"). As of this moment, the 32-bit architecture build queue depth is 1, while the 64-bit architecture build queue depth is 46. That means the 64-bit architecture has a number of source packages on queue to be built (they will have to "wait their turn"). Looking at the 64-bit building computers, there are 3 real 64-bit builders and 3 virtual 64-bit builders. I am curious why the 3 virtual 64-bit builders are not building anything when packages are on queue (although they are not inactive- the last package was built only half an hour ago). Out of these 6 total builders, 1 is for security updates only. Therefore, these 5 builders have to build the binary packages; I hope flashplugin-nonfree's "turn" comes soon.

I'm really confused.

---

### Post by aliencam on 2007-12-15
> **daradib said:**
> May I ask what browser you are using. Are you using Firefox? Try starting firefox from terminal and recording any messages.

actually, after installing ubuntu restricted extras, mplayer, and vlc from synaptic (for different reasons) i decided to try your compiled .deb again and it seems like it is continuing to work now. I will try uninstalling those and seeing if it stops working again.

---

### Post by daradib on 2007-12-15
I'm not exactly sure how it is done on Launchpad, but from what it looks like, Gutsy flashplugin-nonfree 64-bit may be next on the 64-bit builders.

[https://www.launchpad.net/ubuntu/+builds?build_state=pending](https://www.launchpad.net/ubuntu/+builds?build_state=pending)
(Go to the last page or second-to-last page; flashplugin-nonfree dapper-edgy have the lowest build score (number) for amd64)

For the hardy amd64 packages: [https://www.launchpad.net/ubuntu/hardy/amd64/+builds?build_text=&build_state=pending](https://www.launchpad.net/ubuntu/hardy/amd64/+builds?build_text=&build_state=pending)

EDIT: This is correct. The packages were built about 1 or 2 hours after this post, with the hardy packages about 8 hours after this post. See this [post]("http://ubuntuforums.org/showthread.php?p=3962361").

---

### Post by daradib on 2007-12-15
> **aliencam said:**
> actually, after installing ubuntu restricted extras, mplayer, and vlc from synaptic (for different reasons) i decided to try your compiled .deb again and it seems like it is continuing to work now. I will try uninstalling those and seeing if it stops working again.

That's good news. I'm waiting for a response. :cool:

---

### Post by dakuran on 2007-12-15
Hey thx 4 all the work, my flash is now working, w00t w00t, however, it is laggy as hell, i'm talkin REALLY choppy, on youtube and tvliveshows.com, im on gutsy 32bit KDE using firefox Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11, and direct rendering is a YES, i'm on a dell inspiron b130 1.6ghz p3 celeron =[ 1gb ddr, any suggestions? or any further info needed?

Thx in Advance

---

### Post by agmk on 2007-12-16
hey, i've installed the immediate fix without errors (after some trying), and it appears to have worked....but in Firefox, still no Flash. about:plugins indicates gnash is still the .swf plugin.

I did have a lot of trouble with the nspluginwrapper not finding required libraries...which I fixed by removing a pile of stuff and letting the installer install its own dependancies from the repository. I don't know if that's part of the issue or not.

Ubuntu 64-bit (AMD 64 3000), 64 bit Firefox.

Any idea or info needed?

---

### Post by aliencam on 2007-12-16
> **agmk said:**
> hey, i've installed the immediate fix without errors (after some trying), and it appears to have worked....but in Firefox, still no Flash. about:plugins indicates gnash is still the .swf plugin.

I did have a lot of trouble with the nspluginwrapper not finding required libraries...which I fixed by removing a pile of stuff and letting the installer install its own dependancies from the repository. I don't know if that's part of the issue or not.

Ubuntu 64-bit (AMD 64 3000), 64 bit Firefox.

Any idea or info needed?

remove gnash first, do

```
sudo apt-get remove --purge gnash
```

then uninstall the immediate fix flash plugin 

```
sudo apt-get remove --purge flashplugin-nonfree
```

then install again the immediate fix.

---

### Post by daradib on 2007-12-16
The 64-bit Ubuntu flashplugin-nonfree packages have been built by Launchpad for all supported releases about 15 hours ago (9 hours ago for Hardy).

aliencam's instructions were the same as what I had said until I realized that he had already posted an answer (its a race to see who can answer first :-)). However, as Launchpad has built all necessary packages, the immediate fix instructions are obsolete. So when reinstalling the flashplugin-nonfree package, use the official fix instructions.

---

### Post by aliencam on 2007-12-16
official package works great now, thanks for notifying us about it.

---

### Post by daradib on 2007-12-16
> **aliencam said:**
> official package works great now, thanks for notifying us about it.

BTW the official package and the new immediate fix are exactly the same, just immediate fix is compiled by me and official fix by Launchpad.

Cheers.

---

### Post by jstanczak on 2007-12-18
Is this issue fixed? I just installed Xubuntu yesterday and I'm getting this md5sum error:

md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

I didn't even see it in proposed repo. What do I need to do?

---

### Post by pableu on 2007-12-18
Same here, I just wanted to install flashplayer-nonfree in my fresh Ubuntu Gutsy install. Has the tar.gz at Adobe been updated again an broken the MD5-Sum? Or is the fixed version not yet in my repository (ch.archive.ubuntu.com)?

apt-cache says it's Version 9.0.48.0.2+really0ubuntu12.

---

### Post by aliencam on 2007-12-18
as of 2 days ago it is fixed in the repositories, 

try (with firefox closed) 

```

sudo apt-get install flashplugin-nonfree
```

but i guess it *could* be broken again... 

if the repos dont work, try the "imediate fix" in the first post. (download daradib's compiled package)

---

### Post by jstanczak on 2007-12-18
Must be broke again, cause that's what I did and still get the same error.


2900K .......... .......... .......... .......... .......... 99%    1.17 MB/s
 2950K .......... ....                                       100%    1.57 MB/s

15:11:00 (1.56 MB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

---

### Post by DasCrushinator on 2007-12-18
> **aliencam said:**
> as of 2 days ago it is fixed in the repositories, 

try (with firefox closed) 

```

sudo apt-get install flashplugin-nonfree
```

but i guess it *could* be broken again... 

if the repos dont work, try the "imediate fix" in the first post. (download daradib's compiled package)

If you do this, can you still get newer versions by doing a 'sudo aptitude update; sudo aptitude safe-upgrade' or do you have to continue doing the manual installs?

---

### Post by joecrappa on 2007-12-18
I'm still having the same issue, I've tried doing ```
sudo apt-get install flashplugin-nonfree
```

and the install still gives me the same md5sum error. 

DLed the tar.gz from [https://launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/9.0.48.0.2+really0ubuntu12](https://launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/9.0.48.0.2+really0ubuntu12) but I've no idea how to install the tar.gz file. Cannot make deb file from it. 

Any recommendations?

---

### Post by aliencam on 2007-12-18
> **DasCrushinator said:**
> If you do this, can you still get newer versions by doing a 'sudo aptitude update; sudo aptitude safe-upgrade' or do you have to continue doing the manual installs?

i don't know what safe-upgrade is, but if you install something with apt-get it will automatically be upgraded with the update manager. 


[QUOTE=joecrappa] and the install still gives me the same md5sum error.

DLed the tar.gz from [https://launchpad.net/ubuntu/gutsy/+...eally0ubuntu12](https://launchpad.net/ubuntu/gutsy/+...eally0ubuntu12) but I've no idea how to install the tar.gz file. Cannot make deb file from it.

Any recommendations? [/QUOTE] 

the files you linked to are not built yet, you would have to compile them. it's not difficult to do (instructions are in the first post here, under "old" method" but they are already built, so you can get them from apt-get or by (on the left side of the page) clicking on  the build you have (i386 or x64) under "builds"  then downloading the resulting binary.  i would try all the methods in the first post in this topic before doing any of that though.

---

### Post by basementgeek on 2007-12-18
I also still get the md5 error after removing, purging, building, changing repos, trying pre-built debs....etc.

---

### Post by jstanczak on 2007-12-18
I tried a few things but still isn't working. I'll just install the one that's not working and wait for the update.

---

### Post by daradib on 2007-12-18
[https://bugs.launchpad.net/ubuntu/dapper/+source/flashplugin-nonfree/+bug/173890/comments/73](https://bugs.launchpad.net/ubuntu/dapper/+source/flashplugin-nonfree/+bug/173890/comments/73)
> ok , I'm reopening this task as the fix in -proposed was not good for all and has been removed from the archive ( e.g. FF and Konq and Opera ) I have another fix in the works that will be uploaded to -proposed shortly ( before Wednesday hopefully but dont hold me to this )

Please dont add any more "works for me" or "dosent work for me" comments to this bug for now, untill I upload a new version to proposed.

see this Ubuntu-Devel post for more details on the exact situation and possible solutions ( Development wise, not end user solutions )

[https://lists.ubuntu.com/archives/ubuntu-devel/2007-December/024877.html](https://lists.ubuntu.com/archives/ubuntu-devel/2007-December/024877.html)


The packages should still work.

---

### Post by daradib on 2007-12-18
I realized that the 7.10 package was no longer hosted by the repository, so I built two packages (amd64 and i386) myself which I attached to post and linked to.

I have also created backups of the other releases, in case they are removed from being hosting.

I wonder- why were only the 7.10 packages removed.

Anyway, try the updated post, it should now work.

---

### Post by DasCrushinator on 2007-12-18
> **aliencam said:**
> i don't know what safe-upgrade is, but if you install something with apt-get it will automatically be upgraded with the update manager. 


 

the files you linked to are not built yet, you would have to compile them. it's not difficult to do (instructions are in the first post here, under "old" method" but they are already built, so you can get them from apt-get or by (on the left side of the page) clicking on  the build you have (i386 or x64) under "builds"  then downloading the resulting binary.  i would try all the methods in the first post in this topic before doing any of that though.

If you're doing the "fix" you're not really installing it through apt-get though, I thought...

---

### Post by bengar on 2007-12-19
darabid
Thank you very much. I was following all your post about this problem, and your update was useful. The .deb 32-bit packages resolved the youtube, and web pages problem like nick and Disney that need flash to work.

---

### Post by Amphios on 2007-12-19
Same problem here. Installation via official Ubuntu repositories failed because of the md5 checksum error. I will wait for an updated package in the repositories.

---

### Post by jstanczak on 2007-12-19
Could you repost these packages? I'm not finding them. Probably just over looking, thanks.

---

### Post by daradib on 2007-12-19
> **jstanczak said:**
> Could you repost these packages? I'm not finding them. Probably just over looking, thanks.

The list of packages is in the blue text.

> **daradib said:**
> [COLOR="Blue"]**32-bit packages:** The Ubuntu 7.10 package is available [here]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466"). Binary packages for other releases (hosted on Ubuntu repositories): [32-bit 7.04]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.04_i386.deb"), [32-bit 6.10]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.6.10_i386.deb"), and [32-bit 6.06]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.6.06_i386.deb"). Just download the package for your release, double-click the file, and install the package.

**64-bit packages:** The Ubuntu 7.10 package is available [here]("http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466"). Binary packages for other releases (hosted on Ubuntu repositories): [64-bit 7.04]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.04_amd64.deb"), [64-bit 6.10]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.6.10_amd64.deb"), and [64-bit 6.06]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.6.06_amd64.deb"). Just download the package for your release, double-click the file, and install the package. However, I do not believe you will be able to use the 64-bit flashplugin-nonfree package without modifications on Ubuntu releases before 7.10.[/COLOR]

Do you mean that the links don't work? I have tested the links to the packages, and they work.

---

### Post by daradib on 2007-12-19
> **DasCrushinator said:**
> If you're doing the "fix" you're not really installing it through apt-get though, I thought...

Originally, the fix was released through the proposed repository. It, however, was removed due to bug issues (see the apparent problems section of the first post in this thread). That would be through apt-get, because it is on the repository.

Since the package has been removed from the repository, I have provided packages to download and install. All apt-get does is download and install a debian (.deb) package from a repository along with its dependencies. Gdebi (the GUI package installer) installs a downloaded debian package and downloads and installs its dependencies from a repository. As these both use dpkg for managing and installing packages, the underlying system is the same. Apt-get will update the package if the version in the repositories is newer than the installed version.

---

### Post by jstanczak on 2007-12-19
No, I mean I'm can't see, cause I wasn't finding them. Just my bad.
> **daradib said:**
> The list of packages is in the blue text.



Do you mean that the links don't work? I have tested the links to the packages, and they work.

---

### Post by DasCrushinator on 2007-12-19
> **daradib said:**
> Originally, the fix was released through the proposed repository. It, however, was removed due to bug issues (see the apparent problems section of the first post in this thread). That would be through apt-get, because it is on the repository.

Since the package has been removed from the repository, I have provided packages to download and install. All apt-get does is download and install a debian (.deb) package from a repository along with its dependencies. Gdebi (the GUI package installer) installs a downloaded debian package and downloads and installs its dependencies from a repository. As these both use dpkg for managing and installing packages, the underlying system is the same. Apt-get will update the package if the version in the repositories is newer than the installed version.

Ahh, I see, I thought you meant it would some how magically update if someone were to do a fresh install and just go straight to the fix without trying to install flash through the repos.

---

### Post by jstanczak on 2007-12-20
I have flash working now. They work, thanks. So why is there so much trouble for Ubuntu to get this updated? Seems like flash would be a major item in the repo? I mean how many users will just give up on it cause of something so simple?

---

### Post by Blippe on 2007-12-21
Why doesn't the install-script (in the repos deb) throw an error on the md5sum missmatch? And why does it try to connect to a local ftp-server? 


This "piece of code" installs the old (pre-december 2007) version of flash that works in konqueror too, but it has an 64Meg download... Run it line by line in a terminal. 
```
sudo apt-get remove flashplugin-nonfree
wget http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip
unzip fp9_archive.zip  fp9_archive/9r48/install_flash_player_9r48_linux.tar.gz
sudo mkdir /var/cache/flashplugin-nonfree
sudo mv fp9_archive/9r48/install_flash_player_9r48_linux.tar.gz /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz
sudo apt-get install flashplugin-nonfree
rm -r fp9_archive*
```

You're able to uninstall it with synaptic, if a new version comes in the repos it will be upgraded, it actually is exactly as if you installed flash before december, when it all was good.

---

### Post by DasCrushinator on 2007-12-21
> **Blippe said:**
> Why doesn't the install-script (in the repos deb) throw an error on the md5sum missmatch? And why does it try to connect to a local ftp-server? 


This "piece of code" installs the old (pre-december 2007) version of flash that works in konqueror too, but it has an 64Meg download... Run it line by line in a terminal. 
```
sudo apt-get remove flashplugin-nonfree
wget http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip
unzip fp9_archive.zip  fp9_archive/9r48/install_flash_player_9r48_linux.tar.gz
sudo mkdir /var/cache/flashplugin-nonfree
sudo mv fp9_archive/9r48/install_flash_player_9r48_linux.tar.gz /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz
sudo apt-get install flashplugin-nonfree
rm -r fp9_archive*
```

You're able to uninstall it with synaptic, if a new version comes in the repos it will be upgraded, it actually is exactly as if you installed flash before december, when it all was good.

Very cool!  I used this on my PC and laptop and it worked perfect!

---

### Post by anatak23 on 2007-12-21
> **DasCrushinator said:**
> Very cool!  I used this on my PC and laptop and it worked perfect!

Likewise!  Thank you!

---

### Post by mastergunner on 2007-12-22
I just tried the above and it didnt work. I went to youtube and it said I had on old version of flashplayer. Can someone help me. THanks.

---

### Post by zhijian on 2007-12-24
Thanks Daradib (Cyrus Jones). I followed your advice [here]("https://answers.launchpad.net/ubuntu/+question/19584") and now everything works fine. I just tried [YouTube]("http://www.youtube.com") and [Disney]("http://www.disney.com") and they both work perfectly. Thanks and Happy Christmas !

---

### Post by mastergunner on 2007-12-24
zhijian can you explain step by step how you did this? I am new to linux and am having a problem on my amd64 machine. Thanks.

---

### Post by teejay17 on 2007-12-27
> **daradib said:**
> [SIZE=4]**UPDATE: The fix for this bug has been [COLOR=Red]removed[/COLOR] from the proposed repository.**[/SIZE]

It was removed due to major bugs, specifically with Konqueror and Opera (see Apparent Problems with These Fixes).

[CENTER]**[SIZE=3]For a fix, see the built packages (in blue) provided under Main Fix.[/SIZE]**[/CENTER]

This is the support thread for **[Launchpad Bug# 173890]("https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890").** Posts non-developer related should be put in this thread, rather than in the [bug]("https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890") comments to prevent Ubuntu developers from being [flooded by unnecessary information]("https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890/comments/28").

**Bug Symptoms**

The flashplugin-nonfree package fails to install with the following error (viewable only in detailed or verbose mode):
```

md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.
```**Note: If you install the Adobe flash player plugin without viewing the detailed terminal text, the package will appear to be installed, but Flash will not work in Firefox** ([Launchpad Bug# 175255]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/175255")). If one gets repeated messages in Firefox about installing the Adobe Flash Plugin, then this bug is at fault. There is [Lauchpad Bug #175255]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/175255") for the apparent successful installation of a package when the md5sums fail.

This is a very recent bug, caused by [Adobe's update of Flash 9.0 update 3]("http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html") (9.0.115.0) codename "Moviestar" on December 4th.

The change causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). This bug has been [fixed in the next release of Ubuntu (Hardy 8.04)]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2") and it should [soon come as an update to Ubuntu 7.10]("https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890/comments/21").

**Main Fix**

*The statement below is not correct anymore.  The fix for this bug has been [COLOR=Red]removed[/COLOR] from the proposed repository.*

[I]
Currently necessary[/I]: If you do not wish to enable the proposed repository, you may download the binary package alone. Ubuntu 7.10 releases have been built by me as the packages themselves have been removed from the repository (repositories of other releases  still host the packages, but are not referred to)

[COLOR=Blue]**32-bit packages:** The Ubuntu 7.10 package is available [here]("http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466"). Binary packages for other releases (hosted on Ubuntu repositories): [32-bit 7.04]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.04_i386.deb"), [32-bit 6.10]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.6.10_i386.deb"), and [32-bit 6.06]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.6.06_i386.deb"). Just download the package for your release, double-click the file, and install the package.

**64-bit packages:** The Ubuntu 7.10 package is available [here]("http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466"). Binary packages for other releases (hosted on Ubuntu repositories): [64-bit 7.04]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.04_amd64.deb"), [64-bit 6.10]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.6.10_amd64.deb"), and [64-bit 6.06]("http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.6.06_amd64.deb"). Just download the package for your release, double-click the file, and install the package. However, I do not believe you will be able to use the 64-bit flashplugin-nonfree package without modifications on Ubuntu releases before 7.10.[/COLOR]

**Apparent Problems with These Fixes**

These problems are relevant to all of the supplied fixes. That is because all of these fixes are almost identical to each other, all employing Flash 9 Update 3. The fixes are only different packages or sometime just different locations from the same package.

The new version of Flash is incompatible with Konqueror because it requires XEmbed ([Launchpad Bug# 174343]("https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/174343")). 9.0.48.0 is the last version of flash to support Konqueror in its current state.

The new version of Flash is only compatible with 9.50 Beta 2 of Opera (and later).

Some sites, including disney.com and nick.com do not load properly. It would be great if someone tests these sites with an older flash plugin and with Windows Flash Update 3.

On Launchpad Bug Comments, by [selivanow]("https://www.launchpad.net/%7Eselivanow/")


Indeed, Adobe does keep older version of Flash available for download. However, it is not feasible for end users. The only way is through [this archive of flash 9 releases]("http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip") (over 65 MB in size), including installers for all supported platforms).

**Why the packages have been removed from the proposed repository**

[Bug Comment]("https://bugs.launchpad.net/ubuntu/dapper/+source/flashplugin-nonfree/+bug/173890/comments/73"):

[B]
Archived Instructions[/B]


By the way, I am [Cyrus Jones]("https://www.launchpad.net/%7Edaradib") on Launchpad.
Whatever it is you did in the blue box, it works awesome. Thanks so much!!!

---

### Post by zhijian on 2007-12-27
> **mastergunner said:**
> zhijian can you explain step by step how you did this? I am new to linux and am having a problem on my amd64 machine. Thanks.

Master Gunner, I am using an old **32 bit** Dell Desktop but all I did was to follow the steps [here]("https://answers.launchpad.net/ubuntu/+question/19584").


1: I removed the package "flashplugin-nonfree" using the Synaptic Package Manager.

2: I rebooted my system.

3: Then I downloaded [this ]("http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb")package (32-bit only). Installed it, rebooted, and it worked.


Check out the post above for the **64 bit** version (the section with the blue writing).

---

### Post by Smitje on 2007-12-27
Hi there,

The script in the "blue" seems to work fine, (youtube, etc. work) BUT it breaks my updater, when I click the orange star-thingy I get an errormessage telling me to run synaptic. when i do that it points at flashplugin-nonfree as the cause of trouble and insists i uninstall it before it will do any updates.

Thanks for any advise,
Cheers,
Smitje

Oh jah, ... I am on a sparkling new Gutsy 64-bit install, and use Firefox.

EDIT the message looks like this:

Software index is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

---

### Post by sethfc on 2007-12-30
Fix works just fine (working on my parents computer, which I have installed 7.10 32-bit).

FIrefox will still say you need to install a plugin when i'm viewing a youtube video (even tho i dont).

waiting to see if the update issue above is a problem for me

-seth

---

### Post by daradib on 2008-01-02
> **Smitje said:**
> Hi there,

The script in the "blue" seems to work fine, (youtube, etc. work) BUT it breaks my updater, when I click the orange star-thingy I get an errormessage telling me to run synaptic. when i do that it points at flashplugin-nonfree as the cause of trouble and insists i uninstall it before it will do any updates.

Thanks for any advise,
Cheers,
Smitje

Oh jah, ... I am on a sparkling new Gutsy 64-bit install, and use Firefox.

EDIT the message looks like this:

Software index is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

Could you run sudo apt-get install -f in a terminal (Applications -> Terminal) if you have not done so already. What message do you get?

---

### Post by daradib on 2008-01-02
I attached a zip file containing binary packages for Ubuntu 6.06-8.04 (32-bit and 64-bit) to my original post at the start of this thread. If you were not using Ubuntu 7.10, you may not have been able to download a binary package, since the Ubuntu repository does not host those files anymore (it removed the files from the repository before, but continued to host them).

---

### Post by philinux on 2008-01-02
This should be made into a sticky until it's fixed. Anybody doing a reinstall will hit this.

---

### Post by nutz on 2008-01-03
The package worked for me. Thanks for the quick fix.

---

### Post by teejay17 on 2008-01-03
> **philinux said:**
> This should be made into a sticky until it's fixed. Anybody doing a reinstall will hit this.
That's an excellent point; I've already encountered it twice, now.

---

### Post by cionci on 2008-01-03
I would like to signal a bug I filed on launchpad related to flash 9.0.115 and nspluginwrapper in 64 bit Gutsy: [https://bugs.launchpad.net/nspluginwrapper/+bug/177856](https://bugs.launchpad.net/nspluginwrapper/+bug/177856)
I had very often greyed flash animaiton...anyone can confirm ?

---

### Post by sambehera on 2008-01-03
thanks ... ive been trying to install flash on 64 bit gutsy for a long while... this solved it... finally ... no ia32libs and no nspluginwrapper to run flash! ... this worked great

---

### Post by nerdmods on 2008-01-03
Just installed Ubuntu 7.10 32 bit today, updated everything and Firefox's automated install did not work, but downloading the package manually after uninstalling gnash and such, WORKED PERFECTLY!! THANK YOU!!!!!!!!!!


:guitar:

---

### Post by daradib on 2008-01-03
> **cionci said:**
> I would like to signal a bug I filed on launchpad related to flash 9.0.115 and nspluginwrapper in 64 bit Gutsy: [https://bugs.launchpad.net/nspluginwrapper/+bug/177856](https://bugs.launchpad.net/nspluginwrapper/+bug/177856)
I had very often greyed flash animaiton...anyone can confirm ?

Yes, I saw it (I receive flashplugin-nonfree related bugs via email) and posted a [comment]("https://bugs.launchpad.net/nspluginwrapper/+bug/177856/comments/10"):

> I tried the speedtest site and the flash plugin worked for the first test (and I got results), but crashed the second time. I have had flash crash (very occasionally). I'll try the patch, and move this bug to Confirmed soon if nothing comes up.

---

### Post by Smitje on 2008-01-07
hi daradib

>  daradib  	
Re: Bug #173890 flashplugin-nonfree md5 mispatch support thread
[QUOTE]
Originally Posted by Smitje View Post
Hi there,

The script in the "blue" seems to work fine, (youtube, etc. work) BUT it breaks my updater, when I click the orange star-thingy I get an errormessage telling me to run synaptic. when i do that it points at flashplugin-nonfree as the cause of trouble and insists i uninstall it before it will do any updates.

Thanks for any advise,
Cheers,
Smitje

Oh jah, ... I am on a sparkling new Gutsy 64-bit install, and use Firefox.

EDIT the message looks like this:

Software index is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

Could you run sudo apt-get install -f in a terminal (Applications -> Terminal) if you have not done so already. What message do you get?[/QUOTE]

I cant seem to replicate the issue, I tried so many things I should probably consider a fresh gutsy reinstall. However flash now seems to be working fine. thanks!

I am still having trouble getting java to work (at some point it did but now it is bust once again) That is for an other day and an other thread. Thanks for now.

Cheers smitje

---

### Post by cionci on 2008-01-07
> **daradib said:**
> Yes, I saw it (I receive flashplugin-nonfree related bugs via email) and posted a [comment]("https://bugs.launchpad.net/nspluginwrapper/+bug/177856/comments/10"):
Thank you ;)

---

### Post by Double_Thumper on 2008-01-10
Hi Daradib,

In answer to your request: my Firefox/2.0.0.11running under Windows XP Professional SP2 with Adobe Flash Plugin v. 9,0,115,0 shows [http://disney.go.com/index](http://disney.go.com/index) without any apparent problem.

Tonight I will test the fix on my Gutsy desktop at home.

Bye, Lex

---

### Post by Kzin on 2008-01-10
+1 on this thread
Any way to recommend this become a sticky until the "official" package released for Gutsy?

---

### Post by zipperback on 2008-01-12
> **daradib said:**
> Well there does not seem to be any easy way to download old flash plugin from Adobe's website.

The only way is through the following archive of older flash 9 releases (over 65 MB in size)

[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip)

And maybe Macromedia does not permit redistribution of the flash player so it might not be legally possible to only host 9.0.48.0 somewhere else. You should check their license (EULA).



If you are looking for an older version of Flash, you can also download flash 7 which I use to watch youtube videos just fine. There are some sites that require flash 9, but for my purposes, flash 7 works for me.

Here is the link for flash 7.

[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp7_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp7_archive.zip)

- zipperback
:popcorn:

---

### Post by themikedotorg on 2008-01-12
I saw someone else had this problem on another thread, but it applies to using this "fix". I removed firefox and the flashplugin-nonfree and then reinstalled firefox and used the package provided here. It seems to work at first, then the flash videos or site with flash crashes. Here is the code:

> (gecko:12309): Gdk-CRITICAL **: gdk_window_get_toplevel: assertion `obj != NULL' failed
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:12344): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64

(npviewer.bin:12344): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64
ERROR: ld.so: object '/usr/lib/libartsdsp.so.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libartsc.so.0' from LD_PRELOAD cannot be preloaded: ignored.

(npviewer.bin:12365): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64

(npviewer.bin:12365): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libqtengine.so: wrong ELF class: ELFCLASS64
*** NSPlugin Wrapper *** ERROR: NPP_Write() invoke: Message timeout

Using various methods I've found here and ther,, I've gotten this mess of things to work a few times with minimal success. But at least it worked. It isn't working at all now. I don't understand why this is such a problem. 64-bit operating systems and processor architectures have been available for years now. Why won't Adobe (and Sun for that matter) fix their products. The web runs on java and flash now. Its stupid to completely alienate and complicate those of us that want to use the 64-bit processors we paid for.

And I know, I know.. Its licensed, its not free software. Well I don't know anyone thats ever "paid" for flash player or a java runtime environment. They need to get real.

---

### Post by cionci on 2008-01-13
Look at this bug: [https://bugs.launchpad.net/nspluginwrapper/+bug/177856](https://bugs.launchpad.net/nspluginwrapper/+bug/177856)
There's a fixed package of nspluginwrapper.
Please add a replay and tell us if it works and if you have an multi-core CPU.

---

### Post by Zzzach on 2008-01-14
I'm running 64-bit ubuntu 7.10 and I've been trying to get flash working with no luck. I've tried following the advice in this thread but it doesn't seem to fix the problem. Google videos will play but when I try to play them in full screen I get that grey box and then none of the videos will work unless I restart the browser! It's been frustrating. I finally just installed firefox for windows through WINE and at least I can get flash to work through that for now. I hope I can get flash to work though so I don't have to run firefox through wine all the time! :(

---

### Post by Jeffrae on 2008-01-15
Thanks.

The original post worked like a champ fo rmy 32  bit installation.

Jeff P

---

### Post by themikedotorg on 2008-01-15
cionci,
Thank you. That nswrapper package from the link you provided seemed to do the job. At least it isn't crashing now. Hasn't yet, anyway. Yes, I have an AMD Athlon X2.

---

### Post by mario.kostelac on 2008-01-15
Thank you a lot... I have just installed a fresh Gutsy gibbon ant hoopla... flash doesn't work... thank you one more time

---

### Post by cionci on 2008-01-15
> **Zzzach said:**
> I'm running 64-bit ubuntu 7.10 and I've been trying to get flash working with no luck. I've tried following the advice in this thread but it doesn't seem to fix the problem. Google videos will play but when I try to play them in full screen I get that grey box and then none of the videos will work unless I restart the browser! It's been frustrating. I finally just installed firefox for windows through WINE and at least I can get flash to work through that for now. I hope I can get flash to work though so I don't have to run firefox through wine all the time! :(
Try the patched nspluginwrapper posted here: [https://bugs.launchpad.net/nspluginwrapper/+bug/177856](https://bugs.launchpad.net/nspluginwrapper/+bug/177856)

---

### Post by sjkx on 2008-01-16
> **daradib said:**
> Originally, the fix was released through the proposed repository. It, however, was removed due to bug issues (see the apparent problems section of the first post in this thread). That would be through apt-get, because it is on the repository.

Since the package has been removed from the repository, I have provided packages to download and install. All apt-get does is download and install a debian (.deb) package from a repository along with its dependencies. Gdebi (the GUI package installer) installs a downloaded debian package and downloads and installs its dependencies from a repository. As these both use dpkg for managing and installing packages, the underlying system is the same. Apt-get will update the package if the version in the repositories is newer than the installed version.
Just wanted say thanks for the post that gave me the final bits of information and confidence to install the flash plugin from the correct *9.0.115*.deb for the fresh (and first) Ubuntu installation I did yesterday on a ~7-year-old(!) Toshiba notebook PC (Satellite 3005-S304, for the record).  Going through several forum threads trying to figure out how to resolve this problem had the side effect of learning a few useful Linux/Ubuntu sysadmin basics that differ from my Unix experience.

---

### Post by altonbr on 2008-01-17
So why hasn't this been fixed in the Gutsy repositories?

2008-01-17

---

### Post by MarkX on 2008-01-17
Well I'm a very frustrated noob with new and updated 7.10 on 1ghz Duron and just tried to "install missing plugin" on youtube and it still says :
"Hello, you either have Javascript turned off (it's on) or an old version of Adobe's flash player..."
Getting the latest version from adobe and installing it is way beyond my attention span/ ability/ available spare time. Can it be done by GUI, like add/remove applications, or would I have to learn to use the text editor (no chance, like DOS all over again!) ?
 Easy suggestions appreciated.

Edit: BBC news videos don't work either (but do on XP)

---

### Post by nicoladimaria on 2008-01-17
I know it wasn't recommended but I downloaded the big archive and used the file in there, and now works again.

thanks

---

### Post by MarkX on 2008-01-17
> **MarkX said:**
> Well I'm a very frustrated noob with new and updated 7.10 on 1ghz Duron and just tried to "install missing plugin" on youtube and it still says :
"Hello, you either have Javascript turned off (it's on) or an old version of Adobe's flash player..."
Getting the latest version from adobe and installing it is way beyond my attention span/ ability/ available spare time. Can it be done by GUI, like add/remove applications, or would I have to learn to use the text editor (no chance, like DOS all over again!) ?
 Easy suggestions appreciated.

Edit: BBC news videos don't work either (but do on XP)


Aha! Found the "ubuntu restriced formats" thing, really well hidden in add/remove. 
Someone even more of a noob than me would have had no chance of finding that. It should be part of the installation process, with confirmation clicks to licencing agreements.
BBC videos now work, but Adobe flash player doesn't on youtube.

---

### Post by altonbr on 2008-01-17
> **MarkX said:**
> Well I'm a very frustrated noob with new and updated 7.10 on 1ghz Duron and just tried to "install missing plugin" on youtube and it still says :
"Hello, you either have Javascript turned off (it's on) or an old version of Adobe's flash player..."
Getting the latest version from adobe and installing it is way beyond my attention span/ ability/ available spare time. Can it be done by GUI, like add/remove applications, or would I have to learn to use the text editor (no chance, like DOS all over again!) ?
 Easy suggestions appreciated.

Edit: BBC news videos don't work either (but do on XP)

As marked here ([https://answers.launchpad.net/ubuntu/+question/19584](https://answers.launchpad.net/ubuntu/+question/19584)), you can download and install the proper Flash player via: [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

As for BBC, isn't their a big fluff going on right now because they decided to not support Macintosh or Linux users on their website? See if that download works first...

---

### Post by MarkX on 2008-01-18
I got the BBC clips working by installing the (well hidden from noobs) restricted add-ons .

Installed the Adobe player (thanks to help on another thread) by simply downloading their tar.gz file  to the desktop, right-clicking to extract and then clicking the install file. 
I think a lot of linuxers don't know they can do it much faster by GUI too now, without ever typing into  a console (sooo last-century).

---

### Post by altonbr on 2008-01-18
> **MarkX said:**
> I got the BBC clips working by installing the (well hidden from noobs) restricted add-ons .

Installed the Adobe player (thanks to help on another thread) by simply downloading their tar.gz file  to the desktop, right-clicking to extract and then clicking the install file. 
I think a lot of linuxers don't know they can do it much faster by GUI too now, without ever typing into  a console (sooo last-century).

1) I just gave you the .deb to install. You didn't need to use a .tar.gz
2) Using CLI (Command-line) is not "sooo last-century". Can you, with a GUI, install 50 applications, install some fonts, remove some unwanted applications, update and upgrade Ubuntu and perform a backup all in one swoop? I can do so in the CLI which enables me to read a book while it's running...

---

### Post by confy on 2008-01-22
> **daradib said:**
> This fix has bugs when used with Konqueror and Opera (see Apparent Problems with These Fixes).

**Note: If you install the Adobe flash player plugin without viewing the detailed terminal text, the package will appear to be installed, but Flash will not work in Firefox** 

The packet flashplugin-nonfree_9.0.115.0ubuntu0.7.10_amd64.deb works with me on AMD64 machine with firefox.

---

### Post by mdlueck on 2008-01-25
Thanks so much! Worked perfectly for Ubuntu Feisty 7.04!

One question, why was this not updated in the repository but rather it was necessary to download the updated package as linked to by this forum posting? Makes no sense to me why to hide the solution. Even if the new Flash has some issues, a working download is better than a completely busted package in my mind.

---

### Post by daradib on 2008-01-25
> **daradib said:**
> 
**Apparent Problems with These Fixes**

These problems are relevant to all of the supplied fixes. That is because all of these fixes are almost identical to each other, all employing Flash 9 Update 3. The fixes are only different packages or sometime just different locations from the same package.

The new version of Flash is incompatible with Konqueror because it requires XEmbed ([Launchpad Bug# 174343]("https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/174343")). 9.0.48.0 is the last version of flash to support Konqueror in its current state.

The new version of Flash is only compatible with 9.50 Beta 2 of Opera (and later).

Some sites, including disney.com and nick.com do not load properly. It would be great if someone tests these sites with an older flash plugin and with Windows Flash Update 3.

On Launchpad Bug Comments, by [selivanow]("https://www.launchpad.net/~selivanow/")
> Adobe updated the flash plugin. Due to their license, we must download and install their file. This breaks the Gutsy package. We have TWO choices:

1) Don't update the package and have a broken package that no-one can use (aside from the more technically minded)

2) Update the package and have a package that everyone can use, except for konqueror users.

It seems that because we have no control over Adobe, the ball is in konqueror's court and they need to patch. (If their users plan on using flash)

A third solution, if possible, would be to see if Adobe keeps older versions of flash available for download and update the package to pull that.

Indeed, Adobe does keep older version of Flash available for download. However, it is not feasible for end users. The only way is through [this archive of flash 9 releases]("http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp9_archive.zip") (over 65 MB in size), including installers for all supported platforms).

**Why the packages have been removed from the proposed repository**

[Bug Comment]("https://bugs.launchpad.net/ubuntu/dapper/+source/flashplugin-nonfree/+bug/173890/comments/73"):
[QUOTE]
ok , I'm reopening this task as the fix in -proposed was not good for all and has been removed from the archive ( e.g. FF and Konq and Opera ) I have another fix in the works that will be uploaded to -proposed shortly ( before Wednesday hopefully but dont hold me to this )

Please dont add any more "works for me" or "dosent work for me" comments to this bug for now, untill I upload a new version to proposed.

see this Ubuntu-Devel post for more details on the exact situation and possible solutions ( Development wise, not end user solutions )

[https://lists.ubuntu.com/archives/ubuntu-devel/2007-December/024877.html](https://lists.ubuntu.com/archives/ubuntu-devel/2007-December/024877.html)[/QUOTE]

If you want to see very detailed explanations, please read the  [Launchpad bug]("https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890") comments.

---

### Post by mdlueck on 2008-01-25
Yes daradib, those are the bugs I was referring to.

The package currently distributed to 7.04 / 7.10 will not even install due to the md5sum error. What is the point of keeping 7.04 / 7.10 in that completely busted state rather than have to manually download it?

I just thought of one reason... To keep installations currently working from breaking? OK I guess, just a bit of a pain... (shrug)

---

### Post by daradib on 2008-01-25
Yes, you're right.

If they did put an update, Kubuntu (as well as everyone else), would be prompted for update. And Konqueror users would lose flash and have a crashed Konqueror. I guess they could remove the package and put an older package that is stated as an older version (so Synaptic wouldn't upgrade). Or as someone on Launchpad said, a metapackage which conflicts with Konqueror.

---

### Post by rdean on 2008-01-28
@daradib.....

Thank you so much - the following URL worked fine for me:
[http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466](http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466)

Because i am installing a totally new version of Ubuntu, i guess the latest version of Flash Plugin was corrupt as you mentioned. I did as you suggested and everything works fine :)

RD :guitar:

---

### Post by Pekkalainen on 2008-01-30
Im having a really weird issue while trying to solve this problem.
Firefox says I have both flash 7 and 9 installed. How do I remove 7? :confused:

---

### Post by soxs on 2008-01-31
Plx give me some reply, if this page loads completly or crashes on loading as it does on my PC: [http://unrealtournament3.com/de/index.html](http://unrealtournament3.com/de/index.html)

---

### Post by Sentientv2 on 2008-01-31
Thank you very much for putting this together. Made setup a breeze for me.

---

### Post by Sentientv2 on 2008-01-31
> **soxs said:**
> Plx give me some reply, if this page loads completly or crashes on loading as it does on my PC: [http://unrealtournament3.com/de/index.html](http://unrealtournament3.com/de/index.html)

It loads fine on my machine.

---

### Post by daradib on 2008-01-31
> **soxs said:**
> Plx give me some reply, if this page loads completly or crashes on loading as it does on my PC: [http://unrealtournament3.com/de/index.html](http://unrealtournament3.com/de/index.html)

For me, the page does not completely load and it crashes the flash plugin. I am running a 64-bit multicore system. What about you?

---

### Post by daradib on 2008-01-31
The bug that causes the crash is [Launchpad Bug# 177856]("https://bugs.launchpad.net/nspluginwrapper/+bug/177856") and it only affects 64-bit systems, which rely on nspluginwrapper to run the 32-bit flash plugin.

The nspluginwrapper author has provided a patch: [http://launchpadlibrarian.net/11055616/npw.gthreads.diff](http://launchpadlibrarian.net/11055616/npw.gthreads.diff)

And [Rashad Tatum]("https://bugs.launchpad.net/~rmtatum") built a fixed package: [http://launchpadlibrarian.net/11224902/nspluginwrapper_0.9.91.5-1ubuntu2_amd64.deb](http://launchpadlibrarian.net/11224902/nspluginwrapper_0.9.91.5-1ubuntu2_amd64.deb)

EDIT: This bug affects only SMP/SMT machines. Thanks [Riccardo Pellegrini]("https://bugs.launchpad.net/~cionci") and nspluginwrapper author.
(i.e. multicore, multiprocessor, including presumably Intel HyperThreading)

---

### Post by mdlueck on 2008-01-31
> **daradib said:**
> For me, the page does not completely load and it crashes the flash plugin. I am running a 64-bit system. What about you?

I am running Ubuntu 7.04 32-bit edition, Flash via this thread, Firefox via Ubuntuzilla, nVidia binaries via Envy. The page loads fine on my system. Noticeably noisy... eeekkk!!!

---

### Post by daradib on 2008-01-31
OK, so it makes sense that this is indeed Launchpad Bug# 177856.

---

### Post by soxs on 2008-02-01
thx a lot!
Ok, you have to remove the flashplugin-nonfree and the old nspluginwrapper and then install the attached new versions. After this it should work fine.

---

### Post by daradib on 2008-02-01
> **soxs said:**
> thx a lot!
Ok, you have to remove the flashplugin-nonfree and the old nspluginwrapper and then install the attached new versions. After this it should work fine.

You could do that, but I fixed the issue on my computer by simply installing the attached package (which upgrades the older installed package).

---

### Post by Pekkalainen on 2008-02-01
Ok now I have totally purged my system of everything called flash, still firefox uses version 7 without problems, how do I get rid of it? :confused:

Im running gutsy 32 bit

---

### Post by daradib on 2008-02-01
> **Pekkalainen said:**
> Ok now I have totally purged my system of everything called flash, still firefox uses version 7 without problems, how do I get rid of it? :confused:

Im running gutsy 32 bit

Run the following command and output your result.

```
find / -name libflashplayer.so
```

Also, in Firefox address about:plugins what is there about flash.

---

### Post by Pekkalainen on 2008-02-01
> **daradib said:**
> Run the following command and output your result.

```
find / -name libflashplayer.so
```

Also, in Firefox address about:plugins what is there about flash.

about:plugins show flash version 7, thats how I realised it is still installed. 
With that command I found libflashplayer.so in mozillas hidden folder in my home folder, I guess I will try to delete that as well :)
Ah, I also found it in /usr/lib/mozilla/plugins/ , I will delete them all and replace with version 9 to see if that will solve it.

edit: woho, it worked, thanks :D

---

### Post by daradib on 2008-02-02
> **Pekkalainen said:**
> 
edit: woho, it worked, thanks :D

:-)
Always glad to hear it worked. Good luck.

---

### Post by SpiderGorilla on 2008-02-02
> **daradib said:**
> This fix has bugs when used with Konqueror and Opera (see Apparent Problems with These Fixes).
...
**64-bit packages:** The Ubuntu 7.10 package is available [here]("http://ubuntuforums.org/attachment.php?attachmentid=53647&stc=1&d=1198033466"). Just download the package for your release, double-click the file, and install the package. For other releases, download and extract [this archive]("http://ubuntuforums.org/attachment.php?attachmentid=57896") and double-click the corresponding file to your release. However, I do not believe you will be able to use 64-bit flashplugin-nonfree packages without modifications on Ubuntu releases before 7.10.
...
By the way, I am [Cyrus Jones]("https://www.launchpad.net/~daradib") on Launchpad.

Okay, this worked for me on my 7.10 Ubuntu w/ my Dell Inspiron 530 (you can look the specs up yourself, but it's a dual-core 64-bit processor running 4 GIG of RAM). I'm currently running FireFox 2.0.11 as my main system. I've tested speedtest.net, youtube.com and a few other flash-heavy sites and they work great. My previous work-around had been using FireFox 2.0.11 for Windows emulated on Wine. This worked but was very very choppy (video-wise, although audio was okay).

Here's what I had to do first:

1) I used Synaptic Package Manager and installed flashplugin-nonfree as it is currently available. This worked well, except of course for the whole "the plugin isn't installed". For some reason I uninstalled it and then reinstalled it. The nspluginwrapper never did uninstall, even though I marked "complete removal". So that step is probably not at all needed, just me half-following instructions.

2) I used the above link for the .deb file and ran it. It worked fine. My currently installed versions are:

nspluginwrapper: 0.9.91.5-1ubuntu1
flashplugin-nonfree: 0.9.115.0ubuntu0.7

Works fine for me from what I can tell. Disney.com does not work, currently. I just get a grey screen when it attempts to load. Full-screen Flash on YouTube works just fine, no problems. And,  most importantly, my flash games and TheOnion.com all work correctly.

*EDIT* I'd like to make it clear: I **installed** the *non-working* version _first_, THEN installed the above-linked .deb file before it would work. I felt that was important to point out.

---

### Post by MinceMedallion on 2008-02-04
Thankyou, thankyou, thankyou. I was struggling to get either gnash or flash to work on my Ubuntu 7.10 64 bit installation. I uninstalled gnash, then installed your package and hey presto! Flash works in Firefox. I'm grateful for the assistance.

---

### Post by aysiu on 2008-02-05
Since it appears this bug will never be fixed in Ubuntu 7.10, I've created a stop-gap tutorial on installing Flash manually from the Adobe website instead of using the *flashplugin-nonfree* package.

Whenever possible, I've tried to give point-and-click instructions:
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)

---

### Post by Pekkalainen on 2008-02-07
Latest update broke flash on my desktop, guess I will refuse to install it on my laptop wich is now working fine.
edit: aysius guide worked flawlessly after eliminating flashplugin-nonfree

---

### Post by wild77 on 2008-02-07
The latest update also broke my set up as well, it would be nice if they tested these updates before releasing them.

@aysiu thanks for the tip on the manual install, problem solved!

---

### Post by Spenzer4Hire on 2008-02-07
The md5 mismatch issue is a well known problem.  Does the recent Flash update break every install that was working from before Adobe updated their file?

---

### Post by randlieb on 2008-02-08
latest flash non free plugin update caused my flash player to stop working. i downgraded to the previous version and it works again, even in Opera.

---

### Post by Pekkalainen on 2008-02-09
How does one kill updates? Even though I dont have flashplugin-nonfree installed anymore the updater tries to force me to install :confused:

---

### Post by PhilipOwrutsky on 2008-02-12
Still broken for me even after reinstalling...im on a thinkpad T61 running 64 bit 7.10 and here is my cache:

phil@UBUNTUT61:~$ sudo apt-cache policy flashplugin-nonfree info
flashplugin-nonfree:
  Installed: 9.0.48.0.2+really0ubuntu12.2
  Candidate: 9.0.48.0.2+really0ubuntu12.2
  Version table:
 *** 9.0.48.0.2+really0ubuntu12.2 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Packages
        100 /var/lib/dpkg/status
     9.0.48.0.2+really0ubuntu12 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
info:
  Installed: 4.8.dfsg.1-6
  Candidate: 4.8.dfsg.1-6
  Version table:
 *** 4.8.dfsg.1-6 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
        100 /var/lib/dpkg/status


Works for a few seconds after a reboot and then dies :(

---

### Post by soxs on 2008-02-12
In order to make it you work, you should first install the one you get via aptitude/synaptics. the remove --purge them. After that, download the 2 attached packages from this thread (just 1 or 2 pages back).

Note: 8.04 alpha requires still the nspluginwrapper attached in this thread while the flasplayer-nonfree is fixed.

---

### Post by PhilipOwrutsky on 2008-02-12
Ahhhhhh it was nspluginwrapper and not flash directly!?  It seems to be working now (30 min +), but i assume i shouldnt update for a while....Thanks much!

---

### Post by restless on 2008-02-14
daradib
thank you..
i finally managed to fix the flash program.
deleting completely gnash and updating the repositories from the "pre-released updates"


thank you so much.
lor

---

### Post by tidiemme on 2008-02-17
Hi to all!

I just installed ubuntu 7.10 (32bit)

My ver of firefox is 2.0.0.12

I tried these versions:
- the original one from firefox install dialog
- the one from Adobe
- the one from the link on the 1st page of this thread (main fix)
- to downgrade to 9.0.48 with Synaptic

no one works for me!

I miss something?

Thanks

---

### Post by soxs on 2008-02-17
missunderstanding [REMOVED]

---

### Post by daradib on 2008-02-21
> **tidiemme said:**
> Hi to all!

I just installed ubuntu 7.10 (32bit)

My ver of firefox is 2.0.0.12

I tried these versions:
- the original one from firefox install dialog
- the one from Adobe
- the one from the link on the 1st page of this thread (main fix)
- to downgrade to 9.0.48 with Synaptic

no one works for me!

I miss something?

Thanks

Could you give more information, such as the following.

[LIST]
[*]What Firefox displays (specifically regarding Flash) when you type in ```
about:config
``` in the URL box
[*]the current package installed in apt-get, I presume this is 9.0.48.0
[*]the files and folders president in /home/YourUsername/.macromedia (replace YourUsername with your username). including the contents of the directories in that directory
[/LIST]

---

### Post by daradib on 2008-02-21
A notice to everyone.

As a result of [Saïvann Carignan's]("https://www.launchpad.net/~saivann") [bug comment]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/175255/comments/13") on [Launchpad Bug 175255]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/175255"), I recommend everyone to contact Adobe as specified below so that incidents like these will not happen again (i.e. permanent location of flash plugin releases, keep older versions of flash as separate downloads, and/or permission to redistribute the flashplugin binary within Ubuntu).

> I contacted Adobe and they suggest that linux users ask for this [avoid updating the flash plugin without renameing the file (to reflect the version)] at [www.adobe.com/go/wish](www.adobe.com/go/wish)
To every ubuntu users that does not want flashplugin-nonfree to get into problems at each update of flash from adobe, I suggest to ask Adobe to provide permanent links for all recent linux version of flash.

---

### Post by zhkent on 2008-02-28
I've loaded 7.10 on a dell 610 laptop.
I have never been able to get flash to work at pogo.com
youtube works fine.  Test Java Machine web site works.  Have tried purging and installing numerous times.
I get a message do i trust applet, have tried all options here, then java tries to load, but dosen't. 

I tried this      find / -name libflashplayer.so
Here is the output for that and the out put for     sudo find / -name libflashplayer.so


rosie@rosie-laptop:~$ sudo find / -name libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/firefox/plugins/libflashplayer.so
/home/rosie/.Trash/install_flash_player_9_linux/libflashplayer.so
rosie@rosie-laptop:~$ 
rosie@rosie-laptop:~$ 
rosie@rosie-laptop:~$ find / -name libflashplayer.so
find: /proc/tty/driver: Permission denied
find: /proc/1/task/1/fd: Permission denied
find: /proc/1/task/1/fdinfo: Permission denied
and a lot more psrmissions denied.


These are the names and values copied from about:config browser window in firefox;

java.default_java_location_others        /usr/java
java.default_java_location_solaris       /usr/j2se
java.global_java_version_file               /etc/.java/versions
java.java_plugin_library_name        javaplugin_oji
java.private_java_version_file         ~/.java/versions
javascript.allow.mailnews             false
javascript.enabled                     true
javascript.options.showInConsole     false
javascript.options.strict               false

  Thanks for your time and patience if I'm doing something simple wrong.
And thanks for any help on this.

---

### Post by soxs on 2008-02-29
First, if you want find to get all any possible reslut, run it as superuser. Second, if you don't, cut out all the garbage (permission denied.. etc)

What plugin did you try to install? Give Icedtea a try and/or install java6 via the terminal/synapics

---

### Post by zhkent on 2008-03-01
Got java to work by removing GCJ web browser plugin and installing Java SE6 plugin.

---

### Post by piccobello on 2008-04-09
Can anybody tell me which is the most effective place to "lobby" for keeping Konqueror alive? Konqueror is THE reason why I use KDE. It is so much better than firefox, which to me is as "closed" as IE. Plus it works perfect as a file manager and viewer for anything. Dolphin is useless. Gutsy was the first distribution where I could really do anything with konqueror. ok I did not check the disney site ;) but anything else worked so I did not use ffox in a while. After a few updates it started to get painfully slow, and now all flash is broken.

---

### Post by daradib on 2008-04-09
The closest thing I found: [http://brainstorm.ubuntu.com/idea/6290/](http://brainstorm.ubuntu.com/idea/6290/)

You might also want to support Konqueror (there are some Konqueror-specific stuff below):
[http://www.kde.org/support/](http://www.kde.org/support/)
[http://www.kde.org/stuff/buttons.php](http://www.kde.org/stuff/buttons.php)

If you do search queries (i.e. Google) on the Internet, you might be able to find some more things (though you might have already).

---

### Post by mdlueck on 2008-04-14
Your tried and true flashplugin-nonfree_9.0.115.0ubuntu0.7.04_i386.deb package no longer works. I suspect that Adobe has a newer release out now.

Per Adobe's web site... "Adobe Flash Player 9.4 release version 9.0.124.0"

---

### Post by daradib on 2008-04-22
> **mdlueck said:**
> Your tried and true flashplugin-nonfree_9.0.115.0ubuntu0.7.04_i386.deb package no longer works. I suspect that Adobe has a newer release out now.

Per Adobe's web site... "Adobe Flash Player 9.4 release version 9.0.124.0"

Yes, you are correct. I know even before Adobe released the new flash version the md5 hash for the flash plugin changed.

Please use the flashplugin-nonfree package included in Ubuntu; it should work.

---

### Post by mdlueck on 2008-04-22
> **daradib said:**
> Please use the flashplugin-nonfree package included in Ubuntu; it should work.

???? rrrrrr????

The one that is current for 7.04 is for installing Flash 9.0.48.0. I tried again... it fails due to the md5sum error.

The one on this thread is for installing 9.0.115.0 and fails as well.

Now Adobe has released 9.0.124.0 (or maybe even newer since I last checked)

Since you have the md5sum coded into the package, and a particular package will only accept setting up THAT version of Flash, I am puzzled why you thought the 9.0.48.0 installer should suddenly work. Thus: "???? rrrrrr????"

---

### Post by daradib on 2008-04-22
I will look for more information on this.

> **mdlueck said:**
> Since you have the md5sum coded into the package, and a particular package will only accept setting up THAT version of Flash, I am puzzled why you thought the 9.0.48.0 installer should suddenly work. Thus: "???? rrrrrr????"

The new package in Ubuntu operates a little differently than previous packages and the one I have made. It downloads the entire archive of various flash plugin releases, and then installs the specified version. Previously, the package would fetch the default flash plugin on Adobe's website (the latest version) and check if the md5sums are OK. The problem with the older kinds of packages was that it would force Ubuntu to always upgrade its packages to the latest flash plugin releases. This was problematic when Adobe flash plugin version 9.0.115.0 would no longer support Konqueror (since Konqueror did not support XEmbed).

---

### Post by daradib on 2008-04-22
I found you a fix made by [xtknight]("https://www.launchpad.net/~xt-knight").

[https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890/comments/276](https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890/comments/276)

> 

    * [feisty-proposed 9.0.124.0 debdiff]("http://launchpadlibrarian.net/13344211/flashplugin-nonfree_9.0.124.0ubuntu1%7Efeisty1.debdiff") (3.4 KiB, text/plain)

9.0.124.0 update for feisty-proposed

This works in my Feisty VM.

Packages are on my PPA: [https://launchpad.net/~xt-knight/+archive](https://launchpad.net/~xt-knight/+archive)


The fixed package (for 32-bit) for Ubuntu 7.04 is available here: [http://launchpadlibrarian.net/13343812/flashplugin-nonfree_9.0.124.0ubuntu1%7Efeisty1%7Eppa1_i386.deb](http://launchpadlibrarian.net/13343812/flashplugin-nonfree_9.0.124.0ubuntu1%7Efeisty1%7Eppa1_i386.deb)

---

### Post by mdlueck on 2008-04-22
> **daradib said:**
> The new package in Ubuntu...

Where exactly is this "new package" hiding then?

Ubuntu 7.04 shows me 9.0.31.0 is shown as feisty, 9.0.48.0 as feisty-security. And I downloaded 9.0.115.0 from this thread. That is all the version for 7.04 I know of.

---

### Post by daradib on 2008-04-22
> **mdlueck said:**
> Where exactly is this "new package" hiding then.

Ubuntu 7.04 shows me 9.0.31.0 is shown as feisty, 9.0.48.0 as feisty-security. And I downloaded 9.0.115.0 from this thread. That is all the version for 7.04 I know of.

The "new package" is 9.0.48.0.0ubuntu1~7.04.3. Enable the feisty-updates repository to use and then update your package information (Update in Synaptic or sudo apt-get update in terminal). If this doesn't work, you can use the unofficial "fix" referenced in my last post.

You can also install the deb manually (this is the exact same file as the one in the feisty-updates repository)

[https://www.launchpad.net/ubuntu/feisty/i386/flashplugin-nonfree/9.0.48.0.0ubuntu1~7.04.3](https://www.launchpad.net/ubuntu/feisty/i386/flashplugin-nonfree/9.0.48.0.0ubuntu1~7.04.3)

Binary download (32-bit): [http://launchpadlibrarian.net/11815843/flashplugin-nonfree_9.0.48.0.0ubuntu1%7E7.04.3_i386.deb](http://launchpadlibrarian.net/11815843/flashplugin-nonfree_9.0.48.0.0ubuntu1%7E7.04.3_i386.deb)

---

### Post by mdlueck on 2008-04-23
Your suggestion to pull down flashplugin-nonfree_9.0.48.0.0ubuntu1~7.04.3_i386.deb yielded the usual md5sum error.

However, your suggestion to pull down flashplugin-nonfree_9.0.124.0ubuntu1~feisty1~ppa1_i386.deb which I had somehow not seen installed properly. So that is the good package to grab for 7.04 32-bit... for now! ;-)

Thanks so much!

---

### Post by daradib on 2008-04-23
That's great to hear. Cheers! :)

---

### Post by Hooya on 2008-05-03
Looks like this is an issue yet again.  I had flash working just great in Firefox using Hardy 8.04 64-bit, and having installed flash from the package manager.  This morning Flash was working fine, today, nothing.  I get all the classic errors about it already being installed, but none of it works.  I've even tried manually downloading the tar file from Adobe's website (linked from youtube) and putting the .so file in the /plugins directory, and still no avail.  I've purged, and re-downloaded and still nothing.  Even with the proposed repositories enabled I got nothin'

Any idea on how to fix this one?  Again, I'm using 64-bit.

more details:
flashplugin-nonfree_9.0.124.0ubuntu2_amd64.deb is what installs
I don't see the md5sum error anywhere:
```
21:24:48 (522.35 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3044538/3044538]

Download done.
Flash Plugin installed.

```
is the output in the terminal when I run "sudo apt-get install flashplugin-nonfree"

---

### Post by Intelligitimate on 2008-05-09
This doesn't work for me (6.0.6). I still get a md5sum error with the new 9.0.48 repository. I don't know what is going on.

---

### Post by mdlueck on 2008-05-09
> **Intelligitimate said:**
> This doesn't work for me (6.0.6).

The link to an updated package for 7.04:

[https://launchpad.net/~xt-knight/+archive](https://launchpad.net/~xt-knight/+archive)

Seems to only have 7.04 / 7.10 / 8.04 packages.

---

### Post by Intelligitimate on 2008-05-09
Well, what am I supposed to do?

---

### Post by daradib on 2008-05-13
> **Intelligitimate said:**
> Well, what am I supposed to do?

Well, you could try installing the 7.04 package (even though you have a 6.06 system): [http://ppa.launchpad.net/xt-knight/ubuntu/pool/main/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu1~feisty1~ppa1_i386.deb](http://ppa.launchpad.net/xt-knight/ubuntu/pool/main/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu1~feisty1~ppa1_i386.deb)

However, right now I am setting up a prevu environment for dapper (6.06). If you wait, I will build a flashplugin-nonfree package specifically for dapper using the fixed source package from xtknight and the prevu tool (an automatic backporter to build new packages on older releases). Let's see how it goes.

---

### Post by daradib on 2008-05-13
Well I cannot find a way to make 32-bit packages on prevu (I have a 64-bit system).

Try installing the feisty package I linked to in my last post. If that does not work, let me know and I'll try to figure something out.

---

