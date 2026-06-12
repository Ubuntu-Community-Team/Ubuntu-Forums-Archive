---
title: "How to easily delete everything that isn't an mp3 or cover.jpg in a folder?"
date: 2007-01-22
forum: General Help
---

### Post by Royle on 2007-01-22
I just transferred over my music from my windows computer, and the folders are full of files that aren't being used.  The only files worth keeping are either named cover.jpeg or cover.jpg and are mp3s.  How would I easily be able to delete them at once (as there are a lot)?  Any help is greatly appreciated?

---

### Post by gwpritch on 2007-01-22
How about moving everything you want to keep to a secondary folder.

```
 mv /Music/*.mp3  /music/
```

then delete the /Music folder 

```
rm -r /Music
```

'Course if everything is in subfolders, then you're SOL
Depends greatly on the structure of your file tree.

---

