---
title: "date, UTC, GMT, KDE, crashes"
date: 2007-07-19
forum: General Help
---

### Post by kung fu buntu on 2007-07-19
Long story which I've already lost track where exactly did it started but it suffices to tell you this: 
I changed the clock in KDE tray, when I pressed apply X is killed and goes back to KDM. I login and I end up in Gnome, which gets stuck at nautilus initialization, and which needs to be killed with CTRL-ALT-BKSP because clicking logout does nothing. 
Way to go GNU/Linux  :mad:


- BIOS (hardware clock) is set to 23h00 
- hwclock -r ==> 11:00:48 PM UTC 
- date ==> 23:00:53 UTC 
- KDE kcontrol (root | user) ==> 23h00; Current local timezone: Europe/Lisbon (UTC) 
- KDE tray clock ==> 00h00 

I can set KDE tray clock to 23h00 if I set it to UTC. (which is already bugged according to the values from kcontrol) The other problem is that it displays the string "UTC" below the time, but I want it like localtime which displays the string "2007-07-18" instead (but localtime is bugged because its time is 00h). 


Thank you very much for any help!

---

