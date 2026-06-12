---
title: "tranferring firefox profile"
date: 2008-02-24
forum: General Help
---

### Post by Conspirator45 on 2008-02-24
I have recently bought a new laptop. It's running windows vista. I would like to copy my browser configuration to the firefox on the laptop (rss feeds, bookmarks, addons). The older computer is running feisty fawn. How do i go about doing this? TIA

---

### Post by Existentialist on 2008-02-24
Your profiles for firefox are located at:

~/.mozilla/firefox/xxxxxxxx.default/

If you are navigating to it through nautilus, make sure you have it set to show hidden files.  If you copy the contents of this folder in to the default profile folder on the vista laptop, you should have your settings, bookmarks, add-ons, and rss feeds.  For more info on locating the profiles, here is the Mozilla help page about it:

[http://support.mozilla.com/kb/Profiles&bl=y](http://support.mozilla.com/kb/Profiles&bl=y)

---

### Post by bobbybobington on 2008-02-24
Everything should be in a folder with random letters and numbers ending .default (wd4imx8q.default as an example) you can find it under home/"user"/.mozilla/firefox. (the .mozilla folder will be hidden by default in your home user folder, so you'll have to enable it under the view in the file browser). After you copy it into the \Application Data\Mozilla\Firefox\Profiles\ folder in vista.

---

