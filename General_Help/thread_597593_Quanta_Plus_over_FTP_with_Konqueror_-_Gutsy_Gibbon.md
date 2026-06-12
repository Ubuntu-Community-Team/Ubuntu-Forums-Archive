---
title: "Quanta Plus over FTP with Konqueror - Gutsy Gibbon"
date: 2007-10-30
forum: General Help
---

### Post by Tips on 2007-10-30
I installed Gutsy a few days ago.  I like to use Konqueror as an FTP client with the default editor for PHP and CSS files as Quanta Plus.

In earlier versions of Ubuntu, Quanta would edit the files directly over FTP so when I hit Ctrl-s to save the files they would be updated immediately on the server.

In Gutsy, Quanta is downloading the files to a tmp folder and only modifying the remote files when I close Quanta.

Is there a way to change it to the old behavior where the files are loaded directly over FTP instead of being downloaded to a tmp folder?

---

### Post by Tips on 2007-10-30
OK... just figured out the fix... you have to go to:
settings > configure editor > open/save > backup on save ... and then check "remote files"

Then it will save to the remote server.

---

