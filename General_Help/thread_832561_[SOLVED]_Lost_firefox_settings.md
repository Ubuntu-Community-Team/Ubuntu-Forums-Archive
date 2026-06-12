---
title: "[SOLVED] Lost firefox settings"
date: 2008-06-17
forum: General Help
---

### Post by abenco on 2008-06-17
I opened firefox through the terminal window by typing

sudo firefox

and firefox opened correctly. I opened it this way because I was told that the Check for Updates link would be open and it was. I clicked it and it did not find any updates. I went back to the terminal and hit ctrl-c to exit firefox. When I clicked on the firefox link firefox opened but had none of my bookmarks, history, buttons. The back button is never available, like it's not saving the pages I go to. If I open up firefox through the terminal using sudo it opens with all my stuff and works normally, but not when I use the firefox icon or just firefox in the terminal. Any idea what I did or how to fix it?

---

### Post by tamoneya on 2008-06-17
when you open a gui application with sudo it has a possibility of changing the permission on some of your files.  That is why gksudo exists.  From now on you shoudl try to use gksudo firefox instead.  It is probably a simple permissions/ownership issue with the files located in ~/.mozilla.  Take a look at the permissions in this folder by running ```
ls -la ~/.mozilla
```and post the output here.

---

### Post by abenco on 2008-06-17
alexis@J:~$ ls -la ~/.mozilla
total 16
drwx------  4 alexis alexis 4096 2008-04-25 14:10 .
drwxr-xr-x 69 alexis alexis 4096 2008-06-17 17:46 ..
drwx------  3 alexis alexis 4096 2008-04-25 14:10 extensions
drwx------  3 alexis alexis 4096 2008-03-22 17:34 firefox
alexis@J:~$ 


Also noticed that my address bar doesn't change no matter what page I go to. It says [www.gmail.com](www.gmail.com) right now because I typed that in earlier yet I'm obviously not on that page but it never changed when I went to another page. Very weird.

---

### Post by tamoneya on 2008-06-17
hmm that output is the same as mine.  I was expecting it to be owned by root instead of by you.

---

### Post by abenco on 2008-06-17
Thanks for the help

found the answer in [another post]("http://ubuntuforums.org/showthread.php?t=801136")

one line of code fixed it all:
> sudo chown -R <user_name>:<user_name> ~/.mozilla

---

### Post by Colonel_Ingus on 2011-11-05
> **abenco said:**
> Thanks for the help

found the answer in [another post]("http://ubuntuforums.org/showthread.php?t=801136")

one line of code fixed it all:

Just wanted to say this helped me too. I used trickle under sudo to limit firefox's bandwidth momentarily. It seems it changed a few key files to root. I used that command, it took about 2min to complete, it worked.

---

