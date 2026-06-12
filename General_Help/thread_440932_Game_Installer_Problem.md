---
title: "Game Installer Problem"
date: 2007-05-12
forum: General Help
---

### Post by lakerssuperman on 2007-05-12
I used the Doom 3 installer to install the game.  It installed and plays with no problem.  However, I cannot get Quake 4 or Enemy Territory to install.  The installers both crash and say that the md5sum check has failed.  I have tried downloading each installer multiple times from multiple sources with no success.  I am currently running Feisty.  I had previously had Quake 4 running in an Edgy install with no problems.  I thought I just had a corrupt file but after trying both Quake 4 and Enemy territory and getting the same results I think that there may be a larger issue.  Anyone have any idea what the problem could be?

Thanks

---

### Post by baka_rob on 2007-05-13
The md5sum is probably used to verify the install media (CDs, or files it has to download, etc.); since it fails, either the media is bad or the installer is expecting a different set of files.

If it is a downloader, maybe someone updated the game files without updating the md5sum the installer compares them with?  I don't suppose the "installer" is a shell script or other human-readable file, such that users could tell which md5sums it is trying to compare, or which file it thinks is invalid?

---

