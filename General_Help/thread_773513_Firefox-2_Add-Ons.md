---
title: "Firefox-2 Add-Ons"
date: 2008-04-28
forum: General Help
---

### Post by lodp on 2008-04-28
I just upgraded to Hardy and noticed that many add-ons don't work with firefox-3.0. So I thought I'd just downgrade to firefox-2. I did that, but found that many of the add-ons I had installed were greyed out, and I can neither enable them, nor unsinstall/install new ones.

When I click "enable" on one of the greyed-out ones, nothing happens.

When I hit "uninstall", it says "..will be uninstalled when firefox is restarted", but that doesn't happen. The message is still there after a restart.

When I try to install a new add-on I get the following error in the error console:

> Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938

Firefox-3.0 seems to be able to uninstall add-ons just fine.

**EDIT:** Removing the ~/.mozilla/firefox directory (after making a backup of bookmarks.html) seems to have solved the problem. Had to re-install all extensions after that, of course.

Maybe it would have been enough to delete ~/.mozilla/firefox/[identity]/extensions.

Deleting the ~/.xxxx directory of an application really helps quite often if there are problems. Should point that out more often.

---

### Post by newbsawbit on 2008-05-13
I seem to be having the same/similar problem. Haven´t tried uninstalling, but cannot enable in firefox2. I was able to force enabling in firefox 3 w/ nightly tester tools, but would rather just go back to firefox 2 if I could get my extensions to work again.

---

### Post by lodp on 2008-05-14
have you tried doing what i did? don't forget to backup the bookmarks though if you do..

---

### Post by georgedonnelly on 2008-05-14
some of us have large investments in our firefox profiles, signins, special configs, special styles, it goes on and on.

I can't just wipe that away!

Why would you force people to use a beta firefox in a big linux dist like ubuntu?! It makes no sense. ARGH.

---

### Post by lodp on 2008-05-15
DOesn't make much sense to me either.

But as I said:

> Maybe it would have been enough to delete ~/.mozilla/firefox/[identity]/extensions.

so you can try that without losing too much data (all you will lose any extensions and related configs).

---

### Post by siouzi on 2008-05-15
I had similar problem with the extensions and what worked for me was to delete the file **~/.mozilla/firefox/[identity]/extensions.rdf**. Upon restart firefox "relearned" the already installed extensions. Didn't have to reinstall anything and didn't lose any extension settings.

Edit: Also, moving or deleting the extensions directory didn't have any effect in the installed add ons list. Out of curiosity a quick google hit suggests that it should be enough just to do
```
firefox-2 -register
```

This *should* regenerate the extensions.rdf file.

Edit2: Had the problem again on another machine... scratch that register command :/ Deleting the extensions.rdf file worked (for me) again.

---

### Post by felosi on 2008-05-18
Yea same problem here. Happened when I tried to install firefox-2 as I dont like firefox-3 . I did have firefox-2 on here but not the one from apt. Error first started with it, installed apt version - same.

Tried about every fix I seen, Im trying to avoid deleting all extensions. I tried deleting the rdf file and doing the register to no avail. If anyone finds a solution for this please share

---

