---
title: "thunderbird goes on asking to chose a user profile"
date: 2005-07-21
forum: General Help
---

### Post by scorpio2002 on 2005-07-21
Hi there! I can't understand why each time I open Thunderbird it asks me to choose a profile. I only have the default profile and I even checked "Don't aks at startup".

---

### Post by Natja on 2005-07-21
It can happen if thunderbird is already running.

Or is your problem still there when you start thunderbird for the first time ?

---

### Post by scorpio2002 on 2005-07-21
> Or is your problem still there when you start thunderbird for the first time ?

Exactly :|

---

### Post by art on 2005-07-21
check if it's running with

ps aux | grep thunderbird 

.

---

### Post by scorpio2002 on 2005-07-21
Ok, it's running:

```
skorpio  17477  0.0  0.1   3100   760 pts/0    S+   17:04   0:00 grep thunderbird
```

But I didn't open it O_o and if I try to kill it, I get this message: "No such process".

Now, If I run it, I get the following:

```
skorpio  17592  0.0  0.2   3812  1320 ?        S    17:07   0:00 /bin/sh /usr/bin/mozilla-thunderbird -P
skorpio  17628  0.0  0.2   3840  1324 ?        S    17:07   0:00 /bin/sh /usr/lib/mozilla-thunderbird/run-mozilla.sh /usr/lib/mozilla-thunderbird/mozilla-thunderbird-bin -contentLocale en-US -UILocale en-US -P
skorpio  17633  3.6  5.2  83048 27076 ?        Sl   17:07   0:01 /usr/lib/mozilla-thunderbird/mozilla-thunderbird-bin -contentLocale en-US -UILocale en-US -P
skorpio  17663  0.0  0.1   3100   760 pts/0    S+   17:07   0:00 grep thunderbird
```

?_?

---

### Post by art on 2005-07-21
Well the first message you presented means that thunderbird is NOT running, it shows only grep running, that's why it says no such process, when you want to kill it. The second output is exactly the same as mine, if I have thunderbird runnning, so it seems to be allright. Why don't you start the Thunderbird up, check the don't ask at startup icon, logout of GNOME and before logging out check the box save current setup, log back in and see what happens. Another thing I can think of is to create another profile and see if the problem persists.

---

### Post by nix4me on 2005-07-21
Look for a .lck file in the thunderbird dir.  You have to delete the lock file.  Thunderbird does this if it crashes for some reason.

Hope that helps.

---

### Post by Mr Frosti on 2005-07-21
When Thunderbird is in use, it will creat a lock file for your profile. When Thunderbird closes, it is supposed to remove this lock, but it doesn't always. To manually remove the "lock", go to "~/.mozilla-thunderbird/PROFILE NAME/". 

The PROFILE NAME is a randomly generated number, but you should see .default next to it. It will likely be the only profile as well. Inside of this folder, you will see a file called "lock". Make sure Thunderbird is not open, and delete this file:

```
rm ./lock
``` 

Try starting Thunderbird now - it should let you choose the profile you want to use. There will also be a checkbox that you can mark that states "Don't ask at startup". It will use the only profile as the default profile, and will automatically start Thunderbird.

---

### Post by scorpio2002 on 2005-07-22
I know you'll be surprised at hearing this, but Thunderbird creates the lock file when I run it and deletes it when I shout it down. So, this isn't the problem. :|

---

