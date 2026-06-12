---
title: "unable to login to My user account"
date: 2013-08-05
forum: General Help
---

### Post by Saify on 2013-08-05
Dear All
I am ubuntu 12.10 ver user. after some update I am not able to login into my account. after password its again logout. after I created new user which is working fine...
I dont know what is going on...
Help me..
With Best regards..
Saify

---

### Post by thespirit3 on 2013-08-05
I'd log in using the console (ctrl-shift-f1) or using a safe/repair mode from the gui logon screen then rename any config files in your home directory.

I can't remember off the top of my head but something like:-

mv .gconf .gconf.old 
mv .gnome2 .gnome2.old

Then logout, and log in again using the standard login session type (ctrl-alt-f7 if you need to return to the gui).  Gnome/Unity/Whatever will then recreate any config files.

Sorry I can't be more specific, I'm not in front of an ubuntu box.

---

### Post by fdrake on 2013-08-05
at the login screen press ctrl+alt+f2 . use your username and password(of the user that doesn't login).
the reason might be an oversized log file. run this command:
```

rm  .xsession-errors   .xsession-errors.old
sudo shutdown -Pr now

```

---

