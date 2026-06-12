---
title: "&quot;Update LibreOffice is a great idea&quot;, I thought.  Trying to revert and failing!"
date: 2019-07-03
forum: General Help
---

### Post by mikeymikec on 2019-07-03
OS:  Lubuntu 18.04 RTS 64-bit

LibreOffice 6.0.7 was installed, no problems.  However, I fancied getting the latest stable version on (6.1.x), then I noticed weird issues with regard to sorting data in Calc (long delay before the Sort window opened, clicking on column selectors resulted in lots of blank entries, nothing show-stopping but I thought if it's that weird already then weirder things might come out of the woodwork right when I'm trying to get something done quickly).  I tried various things to fix it like reinstalling LO and removing the libreoffice profile data, but it didn't make any difference.  So I thought I'd remove this version and go back to the version I was using.

To get 6.1.x I ran the following commands (gleaned through a bit of googling):

sudo add-apt-repository ppa:libreoffice/libreoffice-6-1
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove

Nothing worrying happened here.

To start the downgrade I removed LO (apt-get remove libreoffice I think?).  I then removed the repository entries.  I then ran apt-get update and tried to install LO but it said that it wasn't going to because of dependencies.  I noticed libreoffce-core was still on 6.1.5 through Synaptic Package Manager so I removed that, then it allowed me to install LO 6.0.7 but only via the console (Synaptic Package Manager refused and cited broken packages but didn't say which ones).

LO 6.0.7 then installed apparently without complaint, the startcenter started OK but clicking on new document or an existing one just crashed LO (the window disappeared).  I tried running through the console but the console output didn't suggest anything untoward had even happened).

Needing LO back up and running quickly, I then decided to revert back to 6.1.5, which has installed OK though the weird sort delay is still there.

Ideally I'd like to go back to a working 6.0.7 setup but I'm not sure what I should do to unfudge it.

---

### Post by deadflowr on 2019-07-03
To downgrade from a PPA version use the package ppa-purge
```
sudo apt install ppa-purge
sudo ppa-purge ppa:libreoffice/libreoffice-6-1
```
ppa-purge removes the ppa version and reverts to the Ubuntu repository version.
More here: [http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html]("http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html")

---

### Post by mikeymikec on 2019-07-04
Thanks, that did the trick.

Was my using the ppa version the most ideal way to install the newer version of LO, or should I have downloaded a deb file from their website?  Do you think there's likely to be any functional difference between the two?

---

### Post by deadflowr on 2019-07-04
PPA is better, imho.
Downloading LibreOffice from The Document Foundation's website downloads a fat archive  file that you then have to extract and install a number of deb files from.
Also, to revert requires a full removal and then reinstallation., whereas ppa-purge clears up ppas in one quick command.
>  Do you think there's likely to be any functional difference between the two?
There shouldn't be any functional differences. 
But then again I don't dig deep enough to find out, myself.

Beyond that if you want to try out new LibreOffice you might try out either the [snap package version]("https://snapcraft.io/libreoffice") or install [flatpak ]("https://flatpak.org/setup/Ubuntu/")and add the flathub repository from which you can install [LibreOffice]("https://flathub.org/apps/details/org.libreoffice.LibreOffice").

The benefit of these two packaging systems is you can install those and keep the normal version as is.
The downsize is that they can load slower first time and are rather restricted within the system, so if you require certain system configurations set it might not be capable.

More on snaps: [https://docs.snapcraft.io/getting-started]("https://docs.snapcraft.io/getting-started")
More on flatpaks: [http://docs.flatpak.org/en/latest/getting-started.html]("http://docs.flatpak.org/en/latest/getting-started.html")

Not to push either packaging system, but I think people should know the options available, warts and all.

---

### Post by mikeymikec on 2019-07-04
Thanks.  Do you think I went about trying to upgrade in the most ideal fashion?  Also, is LO 6.1 likely to come to 18.04 RTS?

I thought the snap version was the latest 'fresh' (as opposed to stable branch) release, ie. "here be monsters, just not as many as a beta/nightly".  Maybe that was me reading into the 'snap' name a little too much (it sounds like it relates to something done quickly) and the instructions I read for it related to 6.2.

Sorry for all the questions, I've been a Windows techie for many years and I'm trying to level up my skills in Linuxville after changing to Lubuntu as my primary OS.

---

### Post by mastablasta on 2019-07-04
snap can be what you or anyone else packs it. in windows imagine it as .exe installer but everything is installed in a *jail.* so the application is contained within it's walls. it is supposed to be more secure like that. but on the other hand it does need more stuff to be packed along with it. Kind of like in windows, only there files from app often install to system folder (when uninstalling it would ask you if you want to remove them).  

maybe these snaps can be thought of as windows portable apps. if you ever used one - they don't need admin access to install, they come with all necessary libraries, don't need access to registry... only snaps are securely contained within some sort of walls.

---

### Post by CatKiller on 2019-07-04
> **mikeymikec said:**
> Also, is LO 6.1 likely to come to 18.04 RTS?

No.

For almost everything, each release has a fixed version. You'll get security fixes, but you won't get new stuff with new features.

There are two exceptions.

Browsers tie together security fixes and new stuff, and often the new stuff is a security fix. You'll get new versions of browsers.

Newer branches of the kernel are necessary for support for new hardware. You'll get security updates for the branch used at release, and newer branches of the kernel, X, and Mesa will be made available through the Hardware Enablement Stack.

Newer versions of random user applications will need a PPA, a container (snaps, flatpaks), or a newer version of Ubuntu.

---

### Post by Dennis N on 2019-07-05
Not mentioned yet is an AppImage. It will get you the newer version you want. I use an AppImage of LibreOffice 6.1.5 on Ubuntu 19.04 - it coexists with the repo version which is from the 6.2.x series. I use the older version because the newer one broke a wanted feature. You need to create a custom .desktop file to make it show up among the other applications (with name slightly changed), but that is easy to do. Google 'AppImage' to learn more.

---

