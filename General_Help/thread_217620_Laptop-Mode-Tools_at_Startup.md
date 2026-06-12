---
title: "Laptop-Mode-Tools at Startup?"
date: 2006-07-17
forum: General Help
---

### Post by tincbtrar on 2006-07-17
Hi everyone!  For some wierd reason, laptop-mode-tools doesnt start on boot.  It only starts after I unplug or plug the computer.  I edited the .conf file to control cpu frequency and ive gotten good results.  I tired to see if there was some sort of script that I could add to startup but to no avail.  Please advise.

Brian.

---

### Post by m83 on 2006-07-17
What do you mean it doesn't start on boot? By default laptop-mode is configured to start at boot, but if it sees that your laptop is connected to AC power, it doesn't make any changes. If your laptop is running on battery when you boot then laptop-mode will lower your CPU frequency, configure HDD standby value, etc. This is perfectly normal.

---

