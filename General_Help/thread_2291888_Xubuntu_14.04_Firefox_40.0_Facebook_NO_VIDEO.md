---
title: "Xubuntu 14.04 Firefox 40.0 Facebook NO VIDEO"
date: 2015-08-23
forum: General Help
---

### Post by tigerdog on 2015-08-23
Ever since Mozilla disabled flash in Firefox, I am unable to view video on Facebook.  I am able to use Firefox 40 on Windows 10 (ugh! not thatI want to) and video works fine without installing flash.  Ideas?

---

### Post by monkeybrain20122 on 2015-08-23
Go to Tools > Addons > Plugins and reset flash to "ask to activate". This should have been reverted already if your flash and FF is up to date. Maybe you should run an update first.

---

### Post by Yellow Pasque on 2015-08-23
From what I gather, Facebook has been using HTML5 for video for a while now. See what this says: [https://www.youtube.com/html5](https://www.youtube.com/html5)

---

### Post by tigerdog on 2015-08-23
> **Temüjin said:**
> From what I gather, Facebook has been using HTML5 for video for a while now. See what this says: [https://www.youtube.com/html5](https://www.youtube.com/html5)
This is what I understood, also.  So why does video not work without Flash?  Should the server/browser negotiate html5 or do I need to change something else, too?

---

### Post by Petro Dawg on 2015-08-23
If you just want the videos to work, I suggest using "[Google Chrome]("http://www.google.com/chrome/")".  I find Firefox has been finicky lately about what it will and won't play anymore.

---

### Post by monkeybrain20122 on 2015-08-23
> **Petro Dawg said:**
> If you just want the videos to work, I suggest using "[Google Chrome]("http://www.google.com/chrome/")".  I find Firefox has been finicky lately about what it will and won't play anymore.

  Everything works here. It is something about OP's settings. Chrome is not the fix all browser, it lost all my tabs, twice.

---

### Post by monkeybrain20122 on 2015-08-23
> **tigerdog said:**
> This is what I understood, also.  So why does video not work without Flash?  Should the server/browser negotiate html5 or do I need to change something else, too?

Try with a new profile. Close FF, open file manager at your home, press ctrl+h or choose show hidden file. Locate the hidden file .mozilla (note the .) rename it to something else say .mozilla-bak, then open FF and try again. To revert back, close FF, delete .mozilla and rename .mozilla-bak back to .mozilla.

---

