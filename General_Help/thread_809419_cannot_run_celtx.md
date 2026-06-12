---
title: "cannot run celtx"
date: 2008-05-27
forum: General Help
---

### Post by woof603 on 2008-05-27
Using Heron, Celtx downloaded to desktop okay, folder opens okay, when I click on "celtx" the run program comes up, but when I click on "run" nothing happens.
Any help, anyone?
Thanks.

---

### Post by dagnabit dang doohickey on 2008-05-27
The instructions to install celtx in this post may help:

[http://ubuntuforums.org/showpost.php?p=3900196&postcount=6](http://ubuntuforums.org/showpost.php?p=3900196&postcount=6)

---

### Post by woof603 on 2008-05-27
Thanks, Doohickey.  This what the link said:

"Installing to /usr/local is odd. Installing to /opt then creating a symbolic link to celtx from /usr/local/bin makes more sense for a program that has a directory full of goodies, as celtx does.


Code:
cd /opt
sudo tar xzvf ~/Desktop/Celtx.tar.gz
cd ~/
sudo ln -s /opt/celtx/celtx /usr/local/bin/celtxCeltx can now be run just by calling celtx instead of /usr/local/celtx/celtx as per your instructions.

BTW: the reason why the first command in the instructions is cd is because tar extracts the archive to the directory that you're currently in."

Could you explain this to me?  I entered the code in the terminal but then what do I do?  How do I activate it?
Sorry to ask such a basic question but I've spent hours reading all the info and I'm just thoroughly confused.
Incidentally, I was entering some other code (also supposedly to get Celtex to run) and it asked for my password which I couldn't supply as the terminal no longer would accept my typing. Any reason?

Many thanks for any more help

---

### Post by dagnabit dang doohickey on 2008-05-27
This code will install celtx into the /opt directory:
```
cd /opt
sudo tar xzvf ~/Desktop/Celtx.tar.gz
```
This will get you back to your home directory:
```
cd ~/
```
And, this code will create a symbolic link in /usr/local/bin for celtx:
```
sudo ln -s /opt/celtx/celtx /usr/local/bin/celtx
```

Now, you can run celtx by hitting Alt+F2, type *celtx* into the box, then hit enter. If you want to create a menu entry and/or desktop shortcut for celtx, the command to enter in those is now *celtx* as well. Its been a couple of years since I used gnome, so I can't give more detail on the menu/shortcut creation process.

BTW: The fist command assumes the celtx download is located on your Desktop.

---

### Post by dagnabit dang doohickey on 2008-05-27
When the terminal requests a password, you won't see the characters as you enter them. This is normal behavior. Just enter your password, hit enter, and you'll be good to go.

---

### Post by woof603 on 2008-05-27
Thanks very much for the info.  I'll work on it in the a.m. and let you know.

---

