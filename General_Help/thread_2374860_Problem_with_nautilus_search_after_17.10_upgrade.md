---
title: "Problem with nautilus search after 17.10 upgrade"
date: 2017-10-19
forum: General Help
---

### Post by shaviro on 2017-10-19
Today I upgraded to 17.10, and everything seems fine except for one thing -- I no longer seem to be able to search for files in nautilus windows. When I enter a search term, it hangs after the first letter I type. Eventually I have to force quit. Any ideas about what I can do?

---

### Post by drs305 on 2017-10-19
Have you checked Files > Preferences: Search & Preview to see if everything looks ok?  You might try limiting the search to only the computer if you have something else selected.

You could also try reinstalling nautilus:
```
sudo apt install --reinstall nautilus
```

---

### Post by shaviro on 2017-10-20
Thanks. Seems to work now

---

