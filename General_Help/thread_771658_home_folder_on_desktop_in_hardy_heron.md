---
title: "home folder on desktop in hardy heron"
date: 2008-04-27
forum: General Help
---

### Post by AvengingAngel718 on 2008-04-27
so i just upgraded to hardy and my desktop icon linking to my home folder no longer works. whenever i click on it it says the application crashed. how do i put a link to my home folder on my desktop in hardy?

---

### Post by ryanhaigh on 2008-04-28
You don't need to create a link, what you should do is press alt-f2 to bring up the run dialog, enter gconf-editor and press enter. When the gconf-editor window pops up press ctrl+f to search, enter volumes as the search term and check both boxes (i use volumes because it i know that will take you to the right place). In the results there should be something about volumes visible, click on that, nearby in the list of options will be show home folder on desktop or something similar, there is also one for voulumes, computer and trash.

Post number 500!!!

---

### Post by AvengingAngel718 on 2008-04-28
seems only slightly more complex than it should be, but it works lol

so, thank you :)

---

