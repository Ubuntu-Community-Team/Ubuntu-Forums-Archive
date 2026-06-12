---
title: "Firefox 3 not saving bookmarks"
date: 2008-05-07
forum: General Help
---

### Post by luke16 on 2008-05-07
Whatever changes I make to my bookmarks (which successfully imported from ff2) are immediately forgotten after I close and reopen FF. It remembers my tabs, but even if I delete or add anything to any of my bookmarks, it is always the same when I reopen firefox.
What is causing this?

---

### Post by luke16 on 2008-05-08
bump

---

### Post by jw5801 on 2008-05-08
I have also had some issues with bookmarks in Firefox 3. As far as I can see Firefox 3 doesn't save bookmarks to the usual place (~/.mozilla/firefox/*.default/bookmarks.html) and I honestly have no idea where it saves them to. My bookmarks update fine, but I have other programs that read the bookmarks from this file. I'm about to try playing around with a few settings in about:config about bookmarks to see if I can make a difference.

---

### Post by the-edmeister on 2008-05-09
luke16,

Try the Firefox Builds forum at MozillaZine for your problem. I don't have access to my notes and links for the MozillaZine KnowledgeBase in the browser I am using right know.

jw5801,

Firefox 3 has an all new setup for bookmarks using an SQLite database system. Bookmarks and history are saved to places.sqlite in the Profile folder, and bookmark backups are saved in the JSON format to the \bookmarkbackups\ folder in the Profile folder. Imported bookmarks, either through an update from Firefox 2.0 or from importing an external *.html file, are in the bookmarks.html file in the Profile folder, which can be kept up-to-date by changing one preference.
Pref Name = **browser.bookmarks.autoExportHTML** - change to True
That pref will increase the shut-down time for Firefox, but you can keep your bookmarks.html file updated for use outside of Firefox 3.0.


Ed

---

### Post by jw5801 on 2008-05-09
> **the-edmeister said:**
> luke16,

Try the Firefox Builds forum at MozillaZine for your problem. I don't have access to my notes and links for the MozillaZine KnowledgeBase in the browser I am using right know.

jw5801,

Firefox 3 has an all new setup for bookmarks using an SQLite database system. Bookmarks and history are saved to places.sqlite in the Profile folder, and bookmark backups are saved in the JSON format to the \bookmarkbackups\ folder in the Profile folder. Imported bookmarks, either through an update from Firefox 2.0 or from importing an external *.html file, are in the bookmarks.html file in the Profile folder, which can be kept up-to-date by changing one preference.
Pref Name = **browser.bookmarks.autoExportHTML** - change to True
That pref will increase the shut-down time for Firefox, but you can keep your bookmarks.html file updated for use outside of Firefox 3.0.


Ed

Cheers, I hadn't had time to really look into it, so I'd manually exported my bookmarks to the old FF2 place, which worked but was annoying when I added any new bookmarks.

---

### Post by Bubba64 on 2008-05-09
When you hit save bookmark from the menu a popup asks you if it wants to save does it say in the folder part bookmarks menu there are 4 different choices. Also if you go to mozilla in your home folder there are backups of what you have saved. This is all of course if FF3 is working correctly.

---

### Post by flavio newbie on 2008-06-12
check that the bookmarks file is not read only at all levels

---

### Post by aysiu on 2008-06-12
Type this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R *username*:*username* ~/.mozilla
``` where *username* is your actual username.

---

### Post by mdewet on 2009-01-08
> **aysiu said:**
> Type this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R *username*:*username* ~/.mozilla
``` where *username* is your actual username.

this solved my bookmark problem, thanks for the tip!

---

### Post by rich.f on 2009-04-09
I'm having a similar problem.  This is with firefox 3.0.8 for ubuntu 8.10 running on an XO (OLPC) laptop, installed via:

[http://www.olpcnews.com/forum/index.php?topic=4053.0](http://www.olpcnews.com/forum/index.php?topic=4053.0)

I posted this already in a reply to that topic on the olpc forum:

[http://www.olpcnews.com/forum/index.php?topic=4053.msg29623#msg29623](http://www.olpcnews.com/forum/index.php?topic=4053.msg29623#msg29623)

but I suspect it's more of an ubuntu/firefox issue, so I'm reposting here.

I can add bookmarks (and bookmark folders) while running firefox, but if I quit and restart, they're gone.  All other user state that I can think of (e.g. history, preferences, cookies) *does* seem to properly persist.

I have checked all of the items mentioned both in this (ubuntuforums) thread, as well as those mentioned here:

[http://ubuntuforums.org/showthread.php?t=319646](http://ubuntuforums.org/showthread.php?t=319646)

All of the files in ~/.mozilla are owned by olpc:olpc, everything is readable by the olpc user, there's only one file (an install.rdf file for an extension) that's not writeable by the olpc user, and all dirs are executable.  Although there is a .parentlock file left behind after quitting firefox, deleting it doesn't help.

I did try the suggestion of setting browser.bookmarks.autoExportHTML to true (via about:config).  If I add a bookmark, when I quit, bookmarks.html *does* get updated with the new bookmark.  When I restart firefox, however, the bookmark is still not there.  Which I guess makes sense, since this is just an html export for convenience.  Also, the next time I quit firefox, the bookmarks (now lacking my previous addition) get rexported, causing the bookmark to disappear from bookmarks.html after the second quit.

Any thoughts?  Am I doing something wrong, or may this be a legitimate bug?

---

### Post by ubername on 2009-04-10
> **rich.f said:**
> I'm having a similar problem.  This is with firefox 3.0.8 for ubuntu 8.10 running on an XO (OLPC) laptop, installed via:

[http://www.olpcnews.com/forum/index.php?topic=4053.0](http://www.olpcnews.com/forum/index.php?topic=4053.0)

...snip

Any thoughts?  Am I doing something wrong, or may this be a legitimate bug?

I have the same symptoms on DellE520, ff3.0.8, jaunty.

---

### Post by rich.f on 2009-04-11
Fwiw, I managed to solve my problem by moving the bookmarkbackups dir within the firefox profile out of the way and having it get automatically recreated.  Further details can be found here:

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/225257/comments/28](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/225257/comments/28)

- Rich

---

### Post by lduvall on 2009-05-02
sudo chown -R username:username ~/.mozilla resolved the problem for me. 

I had upgraded to Ubuntu 9.04 (clean install of / but kept /home) and firefox no longer had any bookmarks, would not save any bookmarks, and would lock up quite nicely on a too regular basis thank you! Things seem to be straightened out now - at least I sure hope so!

---

### Post by neanderthalman on 2009-07-09
> **rich.f said:**
> Fwiw, I managed to solve my problem by moving the bookmarkbackups dir within the firefox profile out of the way and having it get automatically recreated.  Further details can be found here:

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/225257/comments/28](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/225257/comments/28)

- Rich

Thus just fixed the problem for me, Mint 7, FF 3.0.11

---

### Post by confused_user on 2009-07-15
> **neanderthalman said:**
> Thus just fixed the problem for me, Mint 7, FF 3.0.11

yup, worked for me too

---

