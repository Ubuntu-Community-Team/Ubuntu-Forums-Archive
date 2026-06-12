---
title: "[SOLVED] Login script on edubuntu"
date: 2007-11-07
forum: General Help
---

### Post by Tuge on 2007-11-07
i've looked everywhere for solution to my problem and I think this should be quite simple one but yet i have no idea how to solve this: I want to run a script whenever user logins to edubuntu (this is an ltsp server)

What i've tried so far:
I've saved my script to /etc/skel/.test_login
The script runs nicely if run manually

I added the file /etc/skel/.bash_login and added the line to start script -> no result

I checked that whenever user logins .bash_login is copied to /home/USER/ folder

On some point i managed to get it start whenever user started terminal but thats not what i meant to do so no luck there.

please all ideas / solutions are greatly appreciated!

---

### Post by WhistlerUK on 2007-11-07
Tried running it by putting it in the sessions in the system menu?

---

### Post by Tuge on 2007-11-08
thank you for you suggestion, but i've tried that (and it didn't work). and i'm not completely sure if it even should work because of the ltsp thing?!

i'm still struggling with this one -> this is the last thing that keeps me from implementing our first linux server to our campus, so all ideas are greatly valued ...

---

### Post by bodhi.zazen on 2007-11-08
Either put the commands in ~/.bashrc or execute the script from .bashrc

---

### Post by Tuge on 2007-11-09
thanks for your answer!

I tested this and it still does the same. it doesn't run the script on login but on starting the terminal

I made the changes to /etc/skel/.bashrc and checked that it also gets copied to users home folder -> but still its not run on login ... was the file the correct one??

i tried 'sh -x script-name' and it doesn't show any errors

---

### Post by bodhi.zazen on 2007-11-09
Try putting ```
source ~/.bashrc
```

in ~/.bash_profile

---

### Post by Tuge on 2007-11-19
After hundred of tests and LONG search. I placed the script inside /etc/X11/Xsession.d/ and it works like a charm ... Thanks both of you who tried to help me!

---

