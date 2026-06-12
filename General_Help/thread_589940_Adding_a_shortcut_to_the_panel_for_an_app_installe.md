---
title: "Adding a shortcut to the panel for an app installed form a tar.gz"
date: 2007-10-24
forum: General Help
---

### Post by mike868y on 2007-10-24
I recently install instantbird (an im client) from a .tar.gz. I extracted the files to **/usr/lib/instantbird-0.1**. When i browse to this folder and double click the instantbird.sh I get a message asking if i want to run in terminal  display   cancel or run. When i click run the app launches. However when i try and add a shortcut to instantbird.sh on the panel so I can launch it quickly nothing happens? Thanks for the help

---

### Post by mike868y on 2007-10-26
anyone?

---

### Post by thelocust on 2007-10-26
did you chmod u+x instantbird.sh (sorry all I got)

---

### Post by anaconda on 2007-10-26
Sounds familiar. My guess is that the script will try to start a .bin file or another script from the same directory where that script is (or from any directory under it..)

And this wont necessarily work, because when you make a launcher, then running that launcher wont change your "current directory" to be where the script is. And then it cant find the file it is trying to run.

You could edit the script and add to the beginning (backup it first) 
cd /usr/lib/instantbird-0.1

Or even better (because it is not that good idea to edit scripts you dont understand)
make a new script, which would change the directory and launch the other script.
```
#!/bin/bash
cd /usr/lib/instantbird-0.1 && ./instantbird.sh
```
Just open any editor and add the text to it and save it as eg. instantbird_launcher.sh then mark it as executable and give everyone execution and read rights to it. with:
```
chmod a+rx instantbird_launcher.sh
```
and then make the panel shortcut to point to this new script. You can have this new launcher script eg. in your home directory, or in /usr/lib/instantbird-0.1 whatever you prefer. 
PS: make sure the path and the name of the script in the new script are correct. 


The third choise is to add that directory to PATH, so that the script will find the file it tries to run.

Making the launch script is probably the best of these choices.

Hmm. why does this sound so complicated.. it really isn't :)

---

### Post by mike868y on 2007-10-27
thanks for the help.. the script worked...

---

