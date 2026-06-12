---
title: "[Solved] Installing Gnome Power Manager 2.32 (Lucid) issues..."
date: 2013-03-21
forum: General Help
---

### Post by omelette on 2013-03-21
Hi. After realising that the installed GPM 2.30 was using 100's of meg of memory, a search revealed that this was fixed with version 2.32 - but wasn't available for ubuntu 10.04 Lucid. Although I have successfully built GPM 2.32, I get the following warning message during at the './configure' stage;

```
WARNING!!!  GNOME Power Manager uses the "pkexec" utility to provide root
permissions necessary for the "gnome-power-backlight-helper" executable to run.

A link should be provided from the file
"/usr/share/polkit-1/actions/org.gnome.power.policy" to the installed version
"${prefix}/share/polkit-1/actions/org.gnome.power.policy" after installation.

```

Once successfully installed, if I follow the link "/usr/share/polkit-1/actions/org.gnome.power.policy", there is no file named "org.gnome.power.policy" in that folder.  If I reboot or just start GPM, it pops up ever 1-2secs asking for a password, so completely unusable.

Has anyone experienced this and provide a solution?

---

### Post by omelette on 2013-03-22
That turned out a bit of a nightmare.  I managed to somehow break gcc while doing this - ended up with 2 gcc installation folders, 4.4 and 4.4.3, the 4.4.3 folder containing just a single file, but all that was required to convince './configure' that gcc was present but would not create executables.  Turns out that just deleting the 4.4.3 folder & renaming 4.4 to 4.4.3 was all the fixing that was required.  Google to thank for that.

Gnome Power Manager turned out to have additional problems as well.  It's the only package that I have yet come across that refuses to build more than once from a newly-extracted source package, even after issuing 'make clean'.  Once that was out of the way, all that was required was to configure using **'./configure --prefix=/usr'** - no more warning during configure or endless password-prompts when run.

For anyone still with 10.04 & suffering from a similar laptop memory-leak, I've uploaded the build of GPM 2.32 to UbuntuOne and may be downloaded from [here]("http://ubuntuone.com/7YLJdlYVX5f45m8Oad8o2g").  So far it has been running for over 24hrs and is still using the same 2meg of memory it was at launch, which is gratifying to see. :)

BTW, this was (or rather "is", as the '*current*' version is 2.30) an acknowledged bug, details of which may be found [here]("https://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/569273")

---

