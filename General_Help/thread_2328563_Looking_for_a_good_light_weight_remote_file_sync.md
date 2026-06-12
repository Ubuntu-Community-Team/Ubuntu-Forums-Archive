---
title: "Looking for a good light weight remote file sync"
date: 2016-06-22
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2016-06-22
I setup a raspberry pi for my mom to act as a Internet radio
i setup a samba share and mounted it to her music folder on ubuntu
the problem is it is actually much faster to just save the music and copy it over via ssh (took about a hour to rip a single cd compared to under 5 min cause of the share)
what is a good way i can just push all changes in that folder to the pi's music folder
maybe some shell command to watch for changes and they pass them on to the pi, both add/delete
i could just add a button to her panel
i think i should use rsync to pass files and zenity to show a progess/loading bar
i could use owncloud but that just seems overkill for this

---

### Post by HermanAB on 2016-06-22
rsync yes

---

### Post by oldrocker99 on 2016-06-22
> **HermanAB said:**
> rsync yes

Grsync is possibly a little easier to use, with its graphical interface, but either is what you need.

---

### Post by pqwoerituytrueiwoq on 2016-06-26
Since this is for my mom, who is the type of person who has to have a desktop icon for every single little action or cant figure out what to click it needs to be a one click action
```
rsync -r -c --delete-before --info=progress2  ~/Music/ pi@radio.local:~/Music/ | zenity --progress --title "Data Transfer" --text "Syncing Music to Radio..." --percentage=0 --no-cancel --auto-close
```
how do i make zenity read the progress from rsync?

---

