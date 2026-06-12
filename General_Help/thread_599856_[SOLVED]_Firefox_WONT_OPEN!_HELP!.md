---
title: "[SOLVED] Firefox WONT OPEN! HELP!"
date: 2007-11-01
forum: General Help
---

### Post by jckbac9 on 2007-11-01
This is probably really easy to fix, but I cant figure it out. Every time i try to open firefox i get the following message:
"Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."
I have restarted my computer many times and even reinstalled Firefox, but every time i attempt to open it i get that message. 

Thanks,

---

### Post by taurus on 2007-11-01
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ps -A
```

Did you install any plugins/extensions for firefox recently or before all this problem?

---

### Post by BigBoned on 2007-11-01
hey, i get this problem all the time.
all you have to do is:
Terminal>ps x
Find where the firefox process(es) are, and kill them, such as,  "kill 7811"

---

### Post by aysiu on 2007-11-01
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
killall firefox-bin && firefox &
```

---

### Post by jckbac9 on 2007-11-01
wow, thanks for the quick reply. 
however, i have managed to fix the problem. I don't know why I didn't think of it before. I typed "sudo killall firefox-bin", and then firefox opened. 
Again, thanks for the quick reply!:)

---

### Post by jckbac9 on 2007-11-01
sorry aysiu, i typed that last message as you sent yours!

---

### Post by jckbac9 on 2007-11-01
thanks everyone for all the help.

---

