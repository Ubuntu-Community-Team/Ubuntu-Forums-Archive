---
title: "Any tips on hotkeys?"
date: 2008-04-26
forum: General Help
---

### Post by ire on 2008-04-26
Having just made the jump from Windows to Ubuntu, one thing I've been trying to find is an application similar to autohotkey - I used this all the time on Windows when working in SecureCRT - it was great when sending long sh commands to routers and what not.

Anyway, looking for the same in the Ubuntu Terminal - I basically want to be able to map the F keys to text strings, for example:

I hit F6 and this drops into the terminal window   sh run 

Thx in advance!

---

### Post by ryanhaigh on 2008-04-27
This may be useful to you, all you would need to do is change the script that is run to do whatever it is you want. For example if you wanted to open a terminal and execute a command you could use:
```

#!/bin/bash
#start gnome terminal and execute gedit (just an example)
/usr/bin/gnome-terminal -x gedit
exit

```

---

### Post by ryanhaigh on 2008-04-27
This may be useful to you, all you would need to do is change the script that is run to do whatever it is you want. For example if you wanted to open a terminal and execute a command you could use:
```

#!/bin/bash
#start gnome terminal and execute gedit (just an example)
/usr/bin/gnome-terminal -x gedit
exit

```

edit: sorry forgot to include the link [http://ubuntuforums.org/showthread.php?t=759226](http://ubuntuforums.org/showthread.php?t=759226)

---

