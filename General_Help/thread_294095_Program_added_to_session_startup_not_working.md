---
title: "Program added to session startup not working"
date: 2006-11-06
forum: General Help
---

### Post by speedsix on 2006-11-06
I added the command 'alltray firefox' to the sessions startup section. The command works fine in the terminal but doesn't seem to start firefox on startup. How can I suss out why it's not working, all the other programs I have added to startup execute fine.


Thanks

Dom

---

### Post by speedsix on 2006-11-07
Anyone?

---

### Post by jimbob on 2006-11-07
I have no idea of what that command does but it may be that X or gdm is not fully up yet when the command is issued by the task scheduler.

Maybe you could try to add it into rcS or rc.local or something that is farther along in the startup process.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by hikaricore on 2006-11-07
What exactly does this alltray do?

You could make a bash script to sleep for a few seconds then launch it.  This will resolve any issues involving gnome (or kde) not being fully loaded yet.

Open a Terminal and do:

```
sudo pico /bin/xstartup.bash
```

paste this

```

#!/bin/bash
sleep 20
alltray firefox

```

Save the file. (ctrl+o)
Exit. (ctrl+x)

then type:

```
sudo chmod uga+rwx /bin/xstartup.bash
```

Then add /bin/xstartup.bash to your session startup.

This gives your UI 20 seconds to load before launching the process.

Think it may help in your case.

If you're just trying to start firefox when you boot why don't you just put firefox in the session startup?

---

