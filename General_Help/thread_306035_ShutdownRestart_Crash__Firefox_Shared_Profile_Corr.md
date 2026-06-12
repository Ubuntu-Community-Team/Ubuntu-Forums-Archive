---
title: "Shutdown/Restart Crash / Firefox Shared Profile Corruption"
date: 2006-11-24
forum: General Help
---

### Post by PacShady on 2006-11-24
Hey all

Got a strange, but very annoying problem in Kubuntu. Some ground info first: I have a dual-boot system between Kubuntu Dapper and XP, with a FAT32 drive between to swap files between the two. I have a profile on this drive for Firefox and Thunderbird so I can use the same settings, extensions, bookmarks, etc. between the two.

Pretty much since about the time Edgy was released, perhaps as a result of a different setup (after Edgy broke my system and I needed to reinstall Dapper and everything else on it), or perhaps as a result of upgrading to Firefox 2, quite often if I restart my system in Kubuntu, instead of getting the normal Kubuntu shutdown screens (or usually for me for some stupid reason, first half normal console text, THEN normal shutdown screen) I get a black screen with blue and green dotty-line things on it, like theres SOME graphics there but it can't display them, and the computer hangs there.

When I then press my Reset button, and load up either Windows or Kubuntu, I find certain files in my Firefox profile to be corrupted (notably, bookmarks.html, session.rdf, prefs.js, localstore.rdf, and occasionally cookies.txt that I've noticed so far). If I run Firefox, Kubuntu complains of corrupt security settings or something, then displays Firefox with mostly default settings and 90% of my bookmarks missing. In Windows, ALL settings for Firefox and extensions are defaulted, and all bookmarks are missing. The only recovery option for me is to run CHKDSK/FSCK on the drive (so it can remove the corrupted files, they can't be deleted otherwise), and then replace them with backup copies I've started keeping daily since this whole thing started.

Does anyone else share a profile like this over OS's, and has anyone else come up against this problem, either of the Firefox crashing OR Dapper crashing to a black screen with blue and green dotty things across the screen? Or does anyone know what's causing this and how to fix it?

Thanks

'Shady

---

### Post by PacShady on 2006-11-29
*BUMP*

OK, as a temporary fix to my problem, I'm trialling the idea of unmounting the FAT32 drive before shutting down or restarting. Is there a way to make this process automatic? I need to unmount the drive BEFORE KDE and the X server shut down.

Anyone had the same problem as I mention above BTW? Or anyone else know what's causing it or how to fix it? 

'Shady

---

### Post by PacShady on 2006-12-01
* Bump *

---

### Post by PacShady on 2006-12-02
***BUMP***

I take it, either absolutely NO ONE else has this problem, or else there's just so much traffic in this forum that my post keeps getting pushed back and forgotten about. PLEASE HAS ANYBODY GOT IDEAS???

'Shady

---

### Post by PacShady on 2006-12-03
[SIZE="5"]***BUMP***[/SIZE]

I've bumped this 4 times now, and no one has said anything. **PLEASE** does anyone have a clue on what is going on?

'Shady

---

