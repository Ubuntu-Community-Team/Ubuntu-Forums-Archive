---
title: "pymusique 0.5-1~5.04ubp1 broken - here's a fix!"
date: 2005-06-21
forum: General Help
---

### Post by NiceGuyUK on 2005-06-21
Ubuntu update ran this morning and updated my pymusique to version 0.5-1~5.04ubp1 - but when I tried to start the app it came up with an error message and failed to start.

I don't know a lot about Python, but I code in other languages so was able to come up with this fix :-

```
sudo nano -w +166 /usr/bin/pymusique
```

should open the nano editor (easiest for beginners!) with the file loaded and the cursor at the right line which looks like this

```
column.set_fixed_width(int(cwidths[4]))
```

Change the 4 to a 3 so the line should now read like this

```
column.set_fixed_width(int(cwidths[3]))
```

save the file by pressing CTRL O then exit nano by pressing CTRL X

You should now be able to launch pymusique

I don't know if this is an Ubuntu specific problem or an upstream one, and I don't have time to find out - I have a day job!

---

