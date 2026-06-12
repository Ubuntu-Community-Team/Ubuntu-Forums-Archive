---
title: "ln to script with relative paths"
date: 2007-12-01
forum: General Help
---

### Post by crazybilly on 2007-12-01
I just downloaded the new Opera weekly as a tarball.  Inside is the binary (in /bin) and a script that calls it (and does other stuff like initialize java and some other stuff, I THINK).

In any case, I'd like to put a shortcut to it on my desktop.  I tried linking, but when I do, the links don't work right, I assume b/c the script runs in ~/Desktop and then looks for ~/Desktop/bin/opera, when it should be looking for ~/Documents/foo/bar/opera/bin/opera.

I tried making a launcher to the script, too, also with no luck--when I double click it, it just opens in gedit.

Am I doing something wrong w/ linking (I tried ln and ln -s) or the launcher or what? Thanks!

---

### Post by jonnymccullagh on 2007-12-01
I don't know if this will be of any help but I felt sorry for you with no replies ;-)
Could you try the following:
# sudo gedit ~/Desktop/doLatestOpera.sh
Paste in something like this:
#!/bin/bash
/home/me/Documents/foo/bar/opera/bin/opera %u

Save and Exit

then at the command line:
chmod a+x ~/Desktop/doLatestOpera.sh

(you need to make any script you write executable - it sounds like you have not done this as the 'script' is opening in a text editor rather than executing for you)

then run the script:
./Desktop/doLatestOpera.sh 

Hope this helps

---

