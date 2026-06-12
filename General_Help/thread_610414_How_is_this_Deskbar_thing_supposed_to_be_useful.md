---
title: "How is this Deskbar thing supposed to be useful?"
date: 2007-11-12
forum: General Help
---

### Post by rainwalker on 2007-11-12
For example, if I search for "afi" this is what I get:
[IMG]http://i153.photobucket.com/albums/s236/thevoiceless/Screenshot-DeskbarApplet.png[/IMG]

There are two problems with this;
1. What's the point of those two actions? Isn't searching for stuff what the deskbar thing is supposed to be for?
2. I have an entire folder (named "AFI") with AFI tracks in it, why is only one listed?

Also, searching for "afi" with Tracker Search Tool only gives me that one result, whereas that "Search for file names like afi" action lists everything. THAT is what I was trying to do in the first place!

Isn't that what the deskbar is for? To search for files?

---

### Post by daengbo on 2007-11-12
You can turn on Tracker Live Search in the Deskbar preferences and the results from tracker will show up in the Deskbar window. I can't answer why Tracker isn't recognizing AFI. Maybe it can't read the metadata. You can also turn on the "Files, Folders, and Places" option in Deskbar. That might help.

---

### Post by rainwalker on 2007-11-12
I have those enabled, which is why I'm so confused:
[IMG]http://i153.photobucket.com/albums/s236/thevoiceless/Screenshot-DeskbarPreferences.png[/IMG]

---

### Post by erfahren on 2007-11-12
interesting. I haven't really tried it yet either. I enabled the Files and Folders Search and searched for "notes". - I'm fond of naming my files "notes_*this*" and "notes_*that*", so I have quite a few scattered throughout my home folder.

 I came up with only 5 files, 3 of which didn't include the word in the name. (I considered it might be using grep in a way but the preferences specifically says "Find files and folders by searching for a name pattern".) 

I'm not very impressed either!

---

### Post by yostral on 2007-11-12
I had the same kind of odd behavior with tracker. I switched to Beagle and all is working perfectly now.

---

### Post by rainwalker on 2007-11-12
How did you go about switching to Beagle?

---

### Post by yostral on 2007-11-13
I installed beagle and python-beagle (for the link with Deskbar). I uninstalled tracker and that's it.

I just had to restart the deskbar to make it know the changes. I activated beagle and beagle-live in deskbar.

Use first the beagle search GUI to make it start the deamon.

---

### Post by rainwalker on 2007-11-13
Alright so I successfully switched to Beagle, but I'm having a problem: it constantly crashes.
I'll do the same search for "afi"
[IMG]http://i153.photobucket.com/albums/s236/thevoiceless/Screenshot-DeskbarApplet-1.png[/IMG]

and it immediately tells me that something crashed
[IMG]http://i153.photobucket.com/albums/s236/thevoiceless/Screenshot-BugBuddy.png[/IMG]

so I submit the bug report
[IMG]http://i153.photobucket.com/albums/s236/thevoiceless/Screenshot-BugBuddy-1.png[/IMG]

but after I close the window, it shows the "AFI" folder!
[IMG]http://i153.photobucket.com/albums/s236/thevoiceless/Screenshot-DeskbarApplet-2.png[/IMG]

Weird!

---

