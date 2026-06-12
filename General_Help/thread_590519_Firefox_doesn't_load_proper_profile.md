---
title: "Firefox doesn't load proper profile"
date: 2007-10-24
forum: General Help
---

### Post by kfrance on 2007-10-24
I did a fresh install of Gutsy today and as I customarily do, I copied my Firefox profiles over to the new OS. Everything seemed fine at first until I tried to open a different profile, with the command > firefox -P <otherprofile> But I got the default profile. If I closed both instances of Firefox and then opened the otherprofile first then when I tried to load the default profile it loaded the otherprofile. So it seems to load whatever profile was loaded previously. What is going on?

---

### Post by alienexplorers on 2007-10-25
Try from terminal
> firefox -P "profilefolder"
put the profilefolder in quotes.

---

### Post by kfrance on 2007-10-30
I tried putting the folder in quotes and starting it. That gave me the same results. I did do
> firefox -no-remote -P profile
and that worked. -no-remote allows you to have multiple session open at once. I don't know why I didn't have this problem in earlier versions of ubuntu and firefox.

---

