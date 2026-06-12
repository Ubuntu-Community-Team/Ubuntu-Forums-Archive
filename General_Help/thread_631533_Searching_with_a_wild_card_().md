---
title: "Searching with a wild card (*)"
date: 2007-12-04
forum: General Help
---

### Post by dethredic on 2007-12-04
I wanted to search for all .mp3 files in a folder, but using *.mp3 did not work. Is there any way I can do this?

---

### Post by pointone on 2007-12-04
```
locate *.mp3
```

---

### Post by dethredic on 2007-12-04
Ok, that does find them, but I know the are all in "My Music", they are just in sub directories, and I would like to be able to see all of them in one linst, and be able to open them.

---

### Post by .nedberg on 2007-12-04
```
find . -iname *mp3
```

Should do it

---

### Post by dethredic on 2007-12-04
What about using the search bar in the window?

---

