---
title: "[SOLVED] Ignore glipper software update"
date: 2008-01-29
forum: General Help
---

### Post by tgecho on 2008-01-29
The current gutsy repo version of Glipper has an insanely frustrating bug that basically makes it impossible to copy/paste images. I discovered that the source (from the repos!) seems to have this problem fixed. Skipping over the question about why the two don't match... What's bugging me at the moment is the fact that Synaptics/Update Manager thinks that the regular version (0.95.1-3) is newer then the from source version (also 0.95.1-3).

The version I currently have installed seems to work fine, and I haven't had any luck with my attempts to upgrade to 1.0, so in the meantime I simply want the updater to ignore this update. Using "Lock Version" in Synaptic doesn't seem to affect the Update Manager.

---

### Post by tgecho on 2008-02-01
Just thought I'd post the solution I came up with. After trying to upgrade to v1.0 again (it installed, but didn't actually work) I used "checkinstall -D" to create a .deb from the source I downloaded from the universe repositories and manually increased the version number to 0.95.1-4.

I'm sure this is a really horrible thing and I won't make a habit of it. But there we go, it seems to have worked, and when an actual update comes through it should overwrite my hacked up copy :)

---

