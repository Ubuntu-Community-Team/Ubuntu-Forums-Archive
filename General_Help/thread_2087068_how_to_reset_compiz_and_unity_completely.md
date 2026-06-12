---
title: "how to reset compiz and unity completely?"
date: 2012-11-22
forum: General Help
---

### Post by foxy123 on 2012-11-22
After the upgrade from 12.04 to 12.10 compiz and unity constantly crash. I tried reinstalling them and using unity-reset programme but it does not totally reset unity and compiz. Compiz and unity do not crash on any other accounts on the laptop so I guess there is something wrong in the config files. So I'd like to completely reset the settings by probably deleting all config files and let the programmes recreate them again but I am not sure where they now are located. Any help is really appreciated.

---

### Post by mc4man on 2012-11-22
Try 
```
 dconf reset -f /org/compiz/ 
```
Then log out/in

---

### Post by foxy123 on 2012-11-24
Nothing works :-( Tried the code above as well as deleting everything with compiz and unity from my home dir. I wonder if it is possible to reset everything?

---

### Post by timsdeepsky on 2012-11-24
Maybe this might help....
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html]("http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html")
[http://itsfoss.com/how-to-reset-unity-and-compiz-in-ubuntu-12-10/]("http://itsfoss.com/how-to-reset-unity-and-compiz-in-ubuntu-12-10/")

---

### Post by Frogs Hair on 2012-11-24
Be sure you have the dconf editor installed as suggested by the Webupd8 link.

---

### Post by foxy123 on 2012-11-25
Thanks a lot, guys but neither of the above has worked for me. It resets compiz probably the problem was not with compiz or unity. Anyway I did a full reset of my user account by logging in as a different admin user, moving /home/myname folder to /home/myname-backup, creating a new /home/myname folder, changing permissions with ```
sudo chown myname:myname /home/myname
```and copying all the stuff I need from the backed up forlder to the new one. So far so good. I am making this thread as solved but may reopen it if the problems actually persists.

---

### Post by timsdeepsky on 2012-11-25
Please check back after while and let us know if this worked please....I would be curious to know what the difference was between 12.04 and 12.10 on this one....

---

### Post by foxy123 on 2012-12-08
> **timsdeepsky said:**
> Please check back after while and let us know if this worked please....I would be curious to know what the difference was between 12.04 and 12.10 on this one....

Everything runs fine now.

---

