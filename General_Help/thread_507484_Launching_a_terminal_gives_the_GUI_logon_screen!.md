---
title: "Launching a terminal gives the GUI logon screen!"
date: 2007-07-23
forum: General Help
---

### Post by oz2kso on 2007-07-23
I've just installed the Xubuntu 7.04, but I can't get a terminal window!
Launching it (Applications > Accessories > Terminal), just give me a new GUI login screen...
Logging in, launches the desktop environment again!
Killing X (shift+ctrl+backspace) doesn't help - just relaunches the login screen!

Does any one have a suggestion for a workaround, or has this kind of Linux disto's become so user-friendly, that one can't get a prompt? ;o)

Thanks
Kenneth

---

### Post by MikeAlmere on 2007-07-23
It's actually crashing your session. I had the same problem and [this thread ]("http://ubuntuforums.org/showthread.php?t=417661")gives the solution. You have to change a setting. For me this also removed other glitces that I didn't even see as problems.

[http://ubuntuforums.org/showthread.php?t=417661](http://ubuntuforums.org/showthread.php?t=417661)

Probably hard to get a command prompt for you. Try switching to another virtual terminal by pressing ctrl-alt-F1, login with your usual login and password. when you're done type exit and then ctrl-alt-F7 to return to your GUI-environment.

---

