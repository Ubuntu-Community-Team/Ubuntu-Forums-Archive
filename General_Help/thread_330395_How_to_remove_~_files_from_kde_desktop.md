---
title: "How to remove *~ files from kde desktop"
date: 2007-01-03
forum: General Help
---

### Post by ghepardo on 2007-01-03
Hi, I have some text file in my desktop (I use kde), but I also have other files with the same name of the text files with a "~" at the end. How can I remove them or make KDE hide them ?

---

### Post by jordanmthomas on 2007-01-03
Not sure how to make KDE ignore them, but you have a few options:
option 1:  right click on desktop, go to behavior and look for an option in there
option 2:  make your text editor not save backups.
option 3:  write a small script (or make a launcher in kicker) that will get rid of all the files with ~ on the end
for example:

```
mkdir ~/bin && cd bin
nano cleanDesktop

```
slap this in there
```

#!/bin/bash
#deletes all backup files from my desktop
rm $HOME/Desktop/*~

```
ctrl-x y enter enter
```
chmod +x cleanDesktop
```

Then, make a launcher somewhere that runs ~/bin/cleanDesktop
...or just the one command that is in the file

---

