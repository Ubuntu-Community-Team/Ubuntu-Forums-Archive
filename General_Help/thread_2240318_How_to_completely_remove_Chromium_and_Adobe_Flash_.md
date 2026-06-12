---
title: "How to completely remove Chromium and Adobe Flash Player?"
date: 2014-08-19
forum: General Help
---

### Post by Al1000 on 2014-08-19
Hi, 

 I have decided to stick with Firefox and its Shockwave Flash Player plugin, and am trying to completely remove Chromium and Adobe Flash Player from Kubuntu 14.04. I have uninstalled Chromium using ''sudo apt-get remove chromium-browser,'' but a search using ''find . -type d | grep chromium'' reveals several results in ''./.cache/chromium'' and ''./.config/chromium.'' Is it safe to manually remove these directories using the ''rm'' command, and/or is there a better way of doing so?

 Also, is there a command for uninstalling Adobe Flash Player, and/or a better way of removing it as well? A search for ''find . -type d | grep adobe'' finds the following:

> ./.adobe
./.adobe/Flash_Player
./.adobe/Flash_Player/AssetCache
./.adobe/Flash_Player/AssetCache/7EVJQ776
./.adobe/Flash_Player/NativeCache
./.adobe/Flash_Player/NativeCache/82BF58606C7B40D200069D908D58F9DA
./.adobe/Flash_Player/NativeCache/82BF58606C7B40D200069D908D58F9DA/30f15a2a

(I searched the internet to find the ''find . -type d | grep'' command, so am not sure if that's the best command or if there's a more appropriate one I should use instead)

Any help much appreciated.

---

### Post by T.J. on 2014-08-20
Those files are your personal settings, not installed files by the package.  You can safely delete those if you wish.  If you want to be certain that you remove all files related to a package, use the "purge" rather than the "remove" option.  Purge functions the same as remove, except that it also removes system configuration files and stale package data.

Good luck.  Please remember to mark the thread closed if it solves your problem. =)

---

### Post by Al1000 on 2014-08-20
Thanks for your response.

Does this apply to the adobe files as well? IOW is it safe to manually delete these adobe files, as well as the chromium files?

---

### Post by T.J. on 2014-08-20
Yes.  100% percent sure as long as the files are in your personal home folder.  From the names you listed, I'd say yes with 99% certainty.

---

### Post by Al1000 on 2014-08-20
Many thanks for your help.

I've deleted the chromium files so will now go ahead and do the same with the adobe files.

---

