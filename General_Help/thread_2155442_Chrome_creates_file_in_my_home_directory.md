---
title: "Chrome creates file in my home directory"
date: 2013-06-18
forum: General Help
---

### Post by MaZaMo on 2013-06-18
Whenever I open chrome an empty libpeerconnection.log is created in my home directory. I constantly have to delete it! What is this from? I've never had issues in the past.

Using 12.04

---

### Post by vasa1 on 2013-06-18
I've been noticing that file (0 bytes for me) as well. I can't remember seeing it before. I do have Google Chrome installed.

Edit: see [https://code.google.com/p/chromium/issues/detail?id=239048](https://code.google.com/p/chromium/issues/detail?id=239048)

---

### Post by MaZaMo on 2013-06-18
I tried reinstalling chrome but it didn't help...

---

### Post by Frogs Hair on 2013-06-18
This directory placement is  something  the Chrome developers need to address. I  created a  folder of the same name so it didn't look so out of place. Trying to hide the file or folder didn't work. I am now experimenting with the Iron browser (Chromium based) again  which doesn't create the log, but requires the libudev0 dependency in 13.04 like Chrome stable.

---

### Post by mcduck on 2013-06-18
If nothing else, you could always use a ".hidden" file to hide it (without having to rename it).

To do that just create a text file called ".hidden" in the same directory, and add any files & directories to that file, one per each line.

Of course that's just a cosmetic fix, and might not work depending on which desktop environment / file manager you use, but it's still better than having the extra file cluttering your home.

---

### Post by Frogs Hair on 2013-06-18
When trying to hide the document adding by a .  a new on was created  upon opening Chrome again so I opted for the folder. (Unity)

---

### Post by mcduck on 2013-06-18
Yeah, renaming the file of course wouldn't work since Chrome would just look for the file using the old name anyway. Which is why I suggested adding it to the ".hidden" file instead of renaming the file itself.

To explain that a bit better, at least Nautilus looks for a file called ".hidden" in each directory, and then hides all the files & directories listed in that file exactly as if the files themselves had been renamed to add the dot to the file names. This allows you to hide things even when renaming them is not an option.

For example I use a ~/.hidden file with a list of some directories which I don't need to see all the time, yet I can't rename or delete them without breaking some functionality:
```
mcduck@Hyperion:~$ cat .hidden
bin
Desktop
Templates
Audiobooks
Podcasts
log
SavedGames
```

---

### Post by OmgItsPixelated on 2013-06-19
Thanks for that tip, hopefully it'll get addressed in an update.

---

### Post by MaZaMo on 2013-06-19
That solution works, with the .hidden file . . . but it's still not where the file was originally meant to be placed. I wonder what happened to mess up the placement. What does that file do, anyway? It's blank.

---

### Post by markbl on 2013-06-19
That is this bug [https://code.google.com/p/chromium/issues/detail?id=239048](https://code.google.com/p/chromium/issues/detail?id=239048). Please go and star it! Sloppy coding like this annoys the heck out of me.

---

### Post by MaZaMo on 2013-06-20
Thanks! I'll make sure to do that.

---

### Post by eshm on 2013-07-18
Thanks to mcduck on the tip. Great stuff!

---

### Post by vasa1 on 2013-07-18
No longer happens with Chrome Version 29.0.1547.22 beta.

---

