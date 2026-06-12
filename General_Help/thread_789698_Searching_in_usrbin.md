---
title: "Searching in /usr/bin"
date: 2008-05-10
forum: General Help
---

### Post by rgeddes on 2008-05-10
I'm working with Eclipse, and in the preferences, you can ask Eclipse to search for web browsers starting from a parent directory.  I asked it to search in the /usr/bin/ directory, and I noticed the search kept going and going... eventually it stopped and gave back a list of browsers it found.  It showed 75 browsers found.  

/usr/bin/firefox
/usr/bin/mozilla
/usr/bin/X11/firefox
/usr/bin/X11/mozilla
... 
/usr/bin/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/firefox

I only have 1 browser... firefox, and the leftovers of mozilla, probably the leftovers of a removed mozilla package.

I found that there is a symlink 

ls -l /usr/bin/ | grep X11
lrwxrwxrwx 1 root   root          1 2007-02-23 16:22 X11 -> .

which took the eclipse search for a ride in circles as it thought it was looking into a new directory every time it open the symlink.  It doesn't affect the find command, though.

Is this symlink necessary?  Somehow it doesn't look like it should be there... 

Richard

---

### Post by pbpersson on 2008-05-10
I checked my Hardy system and in /usr/bin there is a symlink called X11 and it states that it points to a folder

---

