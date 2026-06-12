---
title: "Firefox 2 and Shared Extensions"
date: 2006-10-31
forum: General Help
---

### Post by PacShady on 2006-10-31
Hey all

I've just recently "upgraded" (read: TRIED to upgrade, broke my system, format and reinstall) to Edgy, and am now in the process of setting up everything again.

I'm pleased to see the Firefox package is now more "official"; on Dapper I needed to run the script to install the official version (effectively making TWO versions of Firefox exist at the same time, the official build, and the Debian build).

Anyways, my problem is this: I run a dual-boot system between Kubuntu and Windows XP. I have a large FAT32 drive between them that I use to store downloads and keep settings such as my Firefox and Thunderbird profiles on. However, I've noticed that Firefox in Edgy isn't loading up any of my extensions. My bookmarks and such are working fine, and the extensions work fine on my Windows system which is also running Firefox 2. In my Add-on dialog box, all the compatible extensions have no icons loaded for them, and I can't access any of their preferences and such. Also, I can't install or update new extensions, and I've noticed other minor problems as well. But my main issue at the moment is getting my extensions working (if I need new extensions, I can always install them in Windows for the time being). Any ideas?

'Shady

---

### Post by PacShady on 2006-11-01
Well, I changed back to Dapper, because Edgy just had far too many problems with it that it shouldn't have on a fresh install. But the same problem with Firefox extensions still exists: Firefox 2 just won't work with my extensions in Linux, when it works fine in Windows.

I've tried copying my profile to my home directory, in the hopes that might have changed something and maybe the problem is Firefox having a hard time reading the FAT32 drive, but no change: Bookmarks read fine, extensions are shown to exist but don't have icons and don't work (except for the built-in official ones like Talkback), and Firefox won't properly install new extensions, permanently stating that they will be installed when Firefox is restarted (no matter HOW many hundred times Firefox is actually restarted, or the computer is restarted for that matter). Before the failed upgrade to Edgy, the extensions worked fine under Firefox 1.5.0.7, and if I could uninstall Firefox 2.0 until it works properly in Linux and go back to 1.5.0.7 I would, but turns out the official version installed by the script overrides any version of Firefox installed from repositories. Fun.

Is this just a problem with Firefox 2 for Linux in general, or is it just in Ubuntu that the problem occurs? And has anyone else had problems getting their extensions to work properly?

'Shady

---

### Post by Zeroangel on 2006-11-01
Not me, but I use Swiftfox 2.0 (a speed-optimized version of FF). All I really had to do was download it, unzip it, and symlink to it in /usr/bin . 
It reads all of my extensions just fine.

However, if I were you, I would go into ~/.mozilla/firefox , find the extensions folder, highlight all of the extensions and make them all world-writable, then try to restart FF. Additionally, I would (temporarily) rename the extensions.rdf file and see if that solves my problems.

If that didn't work, I would temporarily clear my Extensions folder and try again. You can also delete your ~/.mozilla/firefox folder and it will be rebuilt from scratch (you will essentially start with a clean slate).

---

### Post by PacShady on 2006-11-01
After several hours of playing around, I finally worked around the problem. But it involved making a new profile, transferring my bookmarks to it, and downloading the extensions again. Frustrating pain that should never have needed to happen, but oh well, at least it works now.

I'm still not trusting of Edgy though, it would hang at shutdown just before the shutdown splash came up, various troubles with Firefox (including but not limited to the problems I've just had here), and after one failed upgrade and a dodgy install, I think I might wait to see how it's like when Edgy+1 comes out. Until then, Dapper does me just fine.

'Shady

---

