---
title: "thunderbird problem"
date: 2006-11-11
forum: General Help
---

### Post by jeffg21 on 2006-11-11
I have just reinstalled my ubuntu. I had saved my thunderbird files, profiles folder, profiles.ini, registry.dat from the previous installation and after I had reinstalled thunderbird I pasted these into the new .mozilla-thunderbird folder. Unfortunately I had forgotten to close the program. Now when I try to open thunderbird I get a message telling me that the program is open or I have to retart the computer. Restarting, uninstalling and reinstalling all does not help. How can I repair the damage and get thunderbird working again.
I am completely new to ubuntu and linux.

---

### Post by timetunnel on 2006-11-11
This probably means that you still have a "lock" file of Thunderbird in your profile backup. First have a look into your new Thunderbird profile in ".mozilla-thunderbird/<gibberish_foldername>" and see if a file called "lock" is there. Delete it (Thunderbird not running!) and start Thunderbird. 

If that doesn't help, have a look into the **backup** of your profile. If you find a lock-file there, delete it and then proceed the following way on you new ubuntu installation:

[LIST]
[*]make sure Thunderbird is **not** running
[*]delete **everything** in ".mozilla-thunderbird" (or make a backup of it, just in case)
[*]copy the backup of your profile to that folder again
[*]now start Thunderbird and see what happens
[/LIST]

---

### Post by rrwo on 2006-11-11
```
mkdir .thunderbird
ln -s .mozilla-thunderbird .thunderbird
```

---

### Post by jeffg21 on 2006-11-12
Thank you for the help. I deleted the profiles in the thunderbird folder and when I restarted thunderbird it worked. It was just a matter of putting in the new profile information.


> **timetunnel said:**
> This probably means that you still have a "lock" file of Thunderbird in your profile backup. First have a look into your new Thunderbird profile in ".mozilla-thunderbird/<gibberish_foldername>" and see if a file called "lock" is there. Delete it (Thunderbird not running!) and start Thunderbird. 

If that doesn't help, have a look into the **backup** of your profile. If you find a lock-file there, delete it and then proceed the following way on you new ubuntu installation:

[LIST]
[*]make sure Thunderbird is **not** running
[*]delete **everything** in ".mozilla-thunderbird" (or make a backup of it, just in case)
[*]copy the backup of your profile to that folder again
[*]now start Thunderbird and see what happens
[/LIST]

---

