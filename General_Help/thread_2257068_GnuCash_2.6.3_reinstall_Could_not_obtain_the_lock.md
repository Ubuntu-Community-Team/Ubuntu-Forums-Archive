---
title: "GnuCash 2.6.3 reinstall: Could not obtain the lock"
date: 2014-12-16
forum: General Help
---

### Post by SlithyTove on 2014-12-16
I recently re-installed 14.10, and with it, all my usual software, including GnuCash. I've used GnuCash happily for years. But since the most recent re-install, every time I run it, I get the error message "GnuCash could not obtain the lock for [path to my data file]".

No other instance of GnuCash is running. I can tell GnuCash to proceed anyway and it runs normally. I can work around the error by deleting GnuCash's LCK file. But GnuCash always creates a new LCK file, and the error comes up again the next time I run the software. The problem seems to be that GnuCash doesn't delete the LCK file when it closes. I close GnuCash in the usual way, via a menu or Control-Q.

I can't find any other mention of this behavior on the web, and no bug reports. I've tried uninstalling GnuCash and reinstalling, no change in behavior. I'm at a loss what to do from here. Any ideas?

---

### Post by amanchesterman on 2014-12-17
I've never had this problem with GnuCash so I can't speak from experience.

However there is an old post here: [http://lists.gnucash.org/pipermail/gnucash-user/2008-August/026329.html](http://lists.gnucash.org/pipermail/gnucash-user/2008-August/026329.html) which describes your predicament and offers a solution.

I'm wondering if, when you re-installed GnuCash, did you first delete the hidden folder .gnucash in your home directory? It's possible that there are some settings there which have messed with your new installation. Generally when I reinstall software I delete the hidden folders because I've had problems with software not operating properly for that reason.

PS if you do delete the .gnucash folder make sure that you have backed up your data safely first!

---

