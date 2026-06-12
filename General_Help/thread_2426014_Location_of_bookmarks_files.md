---
title: "Location of bookmarks files"
date: 2019-09-03
forum: General Help
---

### Post by jmelton on 2019-09-03
Hi everyone,

What is the location of bookmarks.html files? Are they in a consistent location for all browsers (e.g., within some main folder for that particular browser)? I use Brave, and I discovered to my dismay that I was unable to boot up using my internal hard drive this morning or, once I finally did, to do any work without the computer freezing, but I was able to boot into my external hard drive copy of Linux and am working on it now. But I don't have my bookmarks from that drive. Where can I find the file? Thanks for your help!

Jeff Melton

---

### Post by deadflowr on 2019-09-03
Browser profiles (which contain bookmark settings) are usually in a subfolder in the .config directory.
Sometimes, like Firefox, it has it's own directory. 
(Firefox settings are in .mozilla directory, for example)
So brave should either be in .config/brave, or .brave.

These are per user so these directories are in the user's own home folder.

---

### Post by Holger_Gehrke on 2019-09-03
In Firefox there is no bookmarks.html file unless you create one by exporting your bookmarks; then it's wherever you decide to put it. The bookmarks are normally stored in a SQLite3 database-file named places.db in your profile directory (a subdirectory of ~/.mozilla/firefox) in the tables moz_bookmarks and moz_places.

In Chromium -- which Brave is based on AFAIK -- the bookmarks are stored in the file  '~/.config/chromium/Default/Bookmarks'. This file is in JSON (JavaScript Object Notation) format. So I'd expect Brave to have your bookmarks in a folder named something like '~/.config/brave/Default/'.

Holger

---

### Post by SeijiSensei on 2019-09-03
~/.config/BraveSoftware/Brave-Browser/Default/Bookmarks

---

### Post by dragonfly41 on 2019-09-03
Seems that [Brave plus Zotero]("https://forums.zotero.org/discussion/73644/brave-browser-support") might also be a working combination to consider. 

I have Zotero standalone app in Ubuntu which works with Chromium browser connector.

---

### Post by jmelton on 2019-09-03
Thanks deadflowr, I was able to find it with the info you and someone on another forum provided. To be exact, the location is  ~/.config/BraveSoftware/Brave-Browser/Default.

I now see that several people gave the exact answer before I posted this, so thanks to all of you.

---

### Post by jmelton on 2019-09-03
Thanks!

---

### Post by deadflowr on 2019-09-03
If you found the solution then please go ahead and [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

