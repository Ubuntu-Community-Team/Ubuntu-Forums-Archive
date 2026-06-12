---
title: "Programs not staying in startup programs in sessions"
date: 2007-07-09
forum: General Help
---

### Post by EmyrB on 2007-07-09
Hi all

I have a problem with 7.04 in that when I add programs to the startup programs tab in sessions, they don't stay in the list. If I reboot or go back into the session they aren't shown.

Any ideas

Cheers

EmyrB

---

### Post by linuxwizard on 2007-07-09
I have seen others post the same problem but have not seen a fix. Here is 1 thread talking about it. Don't know what else to tell you sorry.

[http://ubuntuforums.org/showthread.php?t=486243](http://ubuntuforums.org/showthread.php?t=486243)

---

### Post by riutaro on 2007-07-14
> **EmyrB said:**
> Hi all

I have a problem with 7.04 in that when I add programs to the startup programs tab in sessions, they don't stay in the list. If I reboot or go back into the session they aren't shown.

Any ideas

Cheers

EmyrB

Hallo **EmyrB**,
I have the same problem with Feisty.  :mad::mad:

I am just wondering where exactly in the file system the operation tries to change: System &#8594; Preferences &#8594; Sessions. Use the Startup Programs tab to add a New.  I am guessing that my system has the wrong permission in the file/folder to be changed.

This is exactly was the cause of a problem I had with changing default applications to open a file.

---

### Post by riutaro on 2007-07-15
Hello again,

I tried the operation below and now I can add new start-up applications!  Yet to me, the command lines are adabracadabras.  :(  Could I ask what those incantations are supposed to do?

Thank you in advance.
Riu

> **aidanr said:**
> try: 
```
sudo chown -R username ~/.config
sudo chgrp -R username ~/.config
sudo chmod -R 755 ~/.config
```
replace username with your username

---

### Post by willz06jw on 2007-09-11
Those incantations change the permissions of the config file (the file that is used to hold what programs to run at startup).  I guess the problem has to do with the sessions/new program not having the permission to write to that file...

---

### Post by kefurd06 on 2007-12-27
i'm having this exact problem and the commands listed in this therad have done no good. again, i add programs to sessions, exit the window, open it again and my additions are gone. needless to say, the added programs don't run when i log in. thanks

---

### Post by linuxwizard on 2007-12-27
kefurd06
Look over this see if this will help.
[https://answers.launchpad.net/ubuntu/+question/12430](https://answers.launchpad.net/ubuntu/+question/12430)

---

### Post by kefurd06 on 2007-12-27
screenlets messed it up alright. thanks for the help.

---

