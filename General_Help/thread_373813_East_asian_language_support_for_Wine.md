---
title: "East asian language support for Wine"
date: 2007-03-01
forum: General Help
---

### Post by aFan on 2007-03-01
This is a plan. I welcome all constructive criticism and ideas.

For some time now i'm using Ubuntu; i went though horay, breezy and at the moment in sticking to dapper (BDW: i find it great that a version is being supported for a longer period of time). I freely admit that linux is much more fun than MS windows! Thus, i'm looking for way to run win native apps on ubuntu and Wine is the tool for it. Now, i'm running many apps on my ubuntu box and i don't have to swich to win anymore; e.g. dvd_decrypter, dvd_shrink, it is possible to install even macromedia_suite_8 (but first u have to install it on a win box and run it afterwards with wine, with some additional regedit). In some cases i still have to fall back to win, which i hope to change in the future.:)

I would like to compile a package, which will add to wine east asian languages! The installation on win is pretty simple 230MB of data is transfers from the win_install_cd to various locations in the windows folder; among those are ttc, fon and dll files (you can't go without those on win, can't you;), with appropriate registries of course). To my information, on win this is the only way - you can't just copy the files - however, i'm confident that it would be possible on wine.

To do list:
1. Establish complete list of files that install for east asian languages
2. Locate the appropriate registry settings
3. Compile an add-on for wine, which installs MS east asian fonts

Add1:
Until now I couldn't locate complete a list of files. I tracked down the fon and ttc files (e.g. msmicho.ttc, msgothic.ttc for japanise), and there are many more left;). My idea is to monitor the installation process, e.g. using wvplayer. Do you have a better idea? What would be the best way to monitor a virtal machine?

Add2:
The problematic registry setting could be deduced manually; e.g. with the comparison of a default install and a modified one. Suggestions?

Add3:
A complete list of files and registries will be the ground for development of a appropriate script. Would Wine developers support such an en devour? Namely, the build in msiexec does not install apploc.msi, which enables foreign language support for non-unicode apps.

This is not much, but it's a start. I'll be thankful for all ideas which would contibute to my project.

Best regards to ALL!

---

