---
title: "Playing FLAC in Amarok???"
date: 2007-05-04
forum: General Help
---

### Post by ghandi69_ on 2007-05-04
I am using Dapper 6.06, and everything has been running fine so far.  I love and use Amarok to play through my rather large music collection, of which 75% of it is mp3.  However, I recently tried to play some of the FLAC files and an error saying "No Audio Channel" or something like that comes up.  

Has anyone heard about this issue where there is a known workaround??  I googled it and I saw some 'temporary' fixes, just wondering if there was out there for solutions.

---

### Post by ghandi69_ on 2007-05-04
Shameless bump....

---

### Post by musicinmybrain on 2007-05-11
Install libxine1-plugins and restart Amarok. If that's not available on Dapper, install libxine-extracodecs instead.

Edit: Hmm, I remember that at one point there was a bug with libxine that Amarok 1.4.1 exposed. If that's your problem, there's a patched version at [http://ubuntuforums.org/showthread.php?p=1252222](http://ubuntuforums.org/showthread.php?p=1252222). You need the update if your libxine is older than 1.1.2.

---

