---
title: "firefox problem (big time)"
date: 2006-09-14
forum: General Help
---

### Post by raul_ on 2006-09-14
Hello there.
Here's what happened.

 I was trying to install KDE on my ubuntu and firefox was running ok. then i logged out so i could log in with the kde session. Well, the kde didn't pop up, so i went back to gnome to launch firefox to see what the problem was. but it was here where it all started. i don't know if it happens to everybody but sometimes i launch firefox, and it won't open. i can see a window saying "starting firefox" but then it disappears and nothing. oh well...

since i had a lot of updates to do, i launched the update manager. all went well, but in the firefox update, it crashed. it said something like "u can't write on the directory blablabla because it also belongs to the firefox package."  I thought "oh that's strange" but anyway, i tried to update firefox via synaptic, and the same thing happened. then i uninstalled firefox, so i could install it again, and luckily, the updated version. removed it, and THEN, when i tried to install firefox, it said that the package did not exist. the name was in the database but the package didn't exist. then i saw another package called "mozilla-firefox" and i thought that maybe it was the same thing. so i installed it..all went well. but i started firefox and guess what:  NO LETTERS AT ALL. so i thought "oh maybe i need to install the fonts" (ok that was stupid but that's not the point). i installed ALL the mozilla firefox packages (that should have been installed automatically by the way) but nothing happened.

 Anyway, i need to install firefox (i'm running on windows right now). Can anybody help here? Is anything wrong with the firefox packages? Btw, i used both synaptic and apt-get, but the result was the same.

---

### Post by raul_ on 2006-09-14
Never mind. Ends up that i had my custom repositories deactivated (i didn't do that though). just activated them again and everything ran perfectly. Sorry for your trouble =\

---

