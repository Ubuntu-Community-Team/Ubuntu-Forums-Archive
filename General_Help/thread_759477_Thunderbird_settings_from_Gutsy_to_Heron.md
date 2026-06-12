---
title: "Thunderbird settings from Gutsy to Heron"
date: 2008-04-19
forum: General Help
---

### Post by allalogie on 2008-04-19
Hi
I have been using Thunderbird on Gutsy for quite a while, and I would now like to transfer all the settings to another computer running Hardy Heron.
I have previously transferred between Gutsy and Gutsy by simply transferring the folders/files, but I really don't know how or where to transfer to Heron. Is there a simple and future proof method of transferring Thunderbird settings between different Ubuntu versions/computers?
I've tried googling but they mainly show methods to transfer from Windows.

Many thanks

Allalogie

---

### Post by ryanhaigh on 2008-04-19
I would assume that the location of the profile settings hasn't changed and so you should just be able to copy the hidden .mozilla-thunderbird folder from your home directory on the Gutsy system to the new hardy system. If this doesn't work then maybe they have changed the location but all you will need to do then is open thunderbird on hardy and create a new profile (its just temporary so dont worry about the detail) then look for a hidden thunderbird directory in your home directory and replace it with the one from gutsy (just delete the temp profile, copy and rename the one from gutsy). 

To view hidden folders/files in nautilus press Ctrl+H or use the setting in the view menu.

---

### Post by allalogie on 2008-04-19
Hi Ryan
Many thanks for the reply. It was creating a new profile in Thunderbird that sorted it. I was then able to copy my files and profiles.ini file into Thunderbird and replace the newly created profile etc.

Thanks again
Allalogie

---

