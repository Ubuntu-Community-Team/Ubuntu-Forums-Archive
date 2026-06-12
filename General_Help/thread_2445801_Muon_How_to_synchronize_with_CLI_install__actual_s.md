---
title: "Muon: How to synchronize with CLI install / actual system state?"
date: 2020-06-19
forum: General Help
---

### Post by GhX6GZMB on 2020-06-19
I recently cleaned up the fonts in /usr/share/fonts/truetype, mainly deleting unwanted fonts, but also installing some new ones.
I did this directly from CLI, simply copying the fonts and associated directories, then setting ownership and rights for same.
Executed sudo fc-cache -f -v
After that, all the font changes are available to LibreOffice etc., all perfect.

In Muon, though, all the old fonts are still marked as installed, and the new fonts are not present. I have a nasty feeling that this could also be the case with CLI-installed programs, but haven't checked.

Does anyone have an idea how to "synchronize" the actual system state and Muon?

---

### Post by guiverc on 2020-06-19
Muon will read the package database, ie. what was installed via package commands (`apt`, `dpkg` etc) and you only removed the end-files added to your system when those packages were installed, so you've not got incomplete packages removed. Personally I add files to that directory too (not my $USER) but I won't delete fonts (except via package manager), only add.

You'll need to remove the packages they were installed with (which may cause other fonts to also be removed if in the same package), which may not be easy unless you know what you removed.  Your alternative (likely easier) is to re-install them, the remove via package tools.  You may have created a 'mine' you'll later trip over if packages are upgraded, or when you next *release-upgrade* time comes. 

 Personally I'd avoid deleting files created by packages (*unless you already know the consequences.. something in my memory tells me what you did has a consequence even if I don't recall what/how; but I've not done what you want since ~2011 (11.04 maybe) so memory is very hazy*).

---

### Post by Impavidus on 2020-06-20
When manually installing fonts, I'd put them in /usr/local/share/fonts. They should be detected there automatically too and it won't interfere with the fonts installed using the package manager in /usr/share/fonts.

---

### Post by monkeybrain20122 on 2020-06-20
I installed kubuntu 20.04 and found that muon didn't work, search did nothing and it appears to be a long standing bug on and off back to xeniel. I just uninstalled it and installed synaptic instead, all problems solved.

---

### Post by GhX6GZMB on 2020-06-20
Thanks to you all.
It seems I've made a bit of a mess for myself here installing fonts with brute force. Live and learn.

As an upside, I've gone through all other past "real" installs (meaning programs), and these have all been done with either Muon, sudo apt install or .deb install packages from the web (eg, Opera), so they should be OK (I think).

Only the fonts are outside the package management and I've decided that I can live with that. I don't foresee major upheavals with future updates, worst case I'll have to install my fonts again.

A program to build a package from my fonts that the install database will recognize/accept would be cool, though.

Thanks again,

ml9104 (who knows just enough to be dangerous :)  )

---

### Post by ajgreeny on 2020-06-20
I am running Lubuntu 20.04 as a test install in VBox and I find muon a bit of a challenge and not nearly as useful as synaptic,

Like monkeybrain20122, I have also installed and use synaptic instead of muon; try it and you may find that there are some extra search filters in the left-hand pane which will help you, though as you simply removed files rather than uninstalled the packages, it may not be able to show what fonts are now missing.

You could find all the fonts currently installed by using synaptic and clicking on the Font sections in the left hand pane, and choose to reinstall them all.  Maybe you can do the same with muon but I do not use it; maybe worth trying.

---

### Post by GhX6GZMB on 2020-06-20
lThamks.
I'm also not very impressed with Muon, but as it's the default package manager in Lubuntu, it's what I've used.
I'll take a look at synaptic, thanks.

---

