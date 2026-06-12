---
title: "Logging another user off via command line"
date: 2006-10-29
forum: General Help
---

### Post by Roger Mudd on 2006-10-29
I have set up my two Ubuntu machines with two accounts each. One for myself and another for my wife. When my wife uses the machine, she usually forgets to log off. I have the screensaver set to lock the screen when active for both accounts. When I return to the machine I am given the option of logging back in as her or switching users. If I switch users, however, her account remains active. Is there any way to safely log her off from the command line in my X session (assuming I switched users to my account)?

---

### Post by rsay on 2006-10-29
I'm not sure about safely, but this will log her off. (She may lose unsaved data, just like if you rebooted when she was in the middle of editing something.) 

use the who command to find out her session pid (It will be the last number listed.)

```
who -u
```

Then you can kill her session.

```
kill <pid>
```

If you check the who command again you'll see that she won't be listed anymore. 

I've had to use this a few times when my kids have left their systems logged on to flash games on the web and the games were using all of the processing cycles.

---

### Post by Roger Mudd on 2006-10-29
Thanks rsay. I'll give that a try next time it happens.
She rarely ever leaves applications open, so I don't think we'll be risking data loss. Just forgets to log out.
I'm assuming the five-digit number in the final column of output from the command *who -u* is the pid. Please let me know if I'm mistaken.

---

