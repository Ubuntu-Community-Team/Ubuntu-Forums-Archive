---
title: "How to open procress in High Priority?"
date: 2008-04-27
forum: General Help
---

### Post by evozniak on 2008-04-27
I'am using wine to play many games but some games heave great performace incriase with set priority to ~-17, i need start wine with this priority.

whow i do this?

---

### Post by olskar on 2008-04-27
with "nice -17" I think

---

### Post by evozniak on 2008-04-27
i can change priority of process runing via comand line?

---

### Post by Monicker on 2008-04-27
> **evozniak said:**
> i can change priority of process runing via comand line?

Yes, you can.

renice -n -20 -p <pid>


Another way to do it is to run top, and then press "r".  You will then be prompted for the pid for which you want to change the priority. Personally I would not start at the highest level; maybe start at -5, then -10, etc.

---

### Post by ryanhaigh on 2008-04-27
You could make a small script to launch wine and then renice the wine process automatically, you can then create a launcher on your desktop (which you could move to the panel/menus) that points to this script.

```

#!/bin/bash
wine /path/to/windows/game &&
renice -n -20 -p `pidof wine` && 
exit

```

Save the code in a file in your home directory (eg .start_gamename.sh). Then use ```
chmod +x .start_gamename.sh
``` to make the script executable.

Then right click on the desktop, create new launcher, use whatever you want for the name and set the command to /home/youusername/.start_gamename.sh

---

