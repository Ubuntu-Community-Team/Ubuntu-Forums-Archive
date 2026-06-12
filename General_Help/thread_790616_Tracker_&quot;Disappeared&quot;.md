---
title: "Tracker &quot;Disappeared&quot;"
date: 2008-05-11
forum: General Help
---

### Post by haelen on 2008-05-11
The Tracker Icon has vanished from my taskbar. When I use Tracker via Accessories --> Tracker Search Tool, I get no results for any query.

TIA,
Tim

---

### Post by quibbler on 2008-05-12
> **haelen said:**
> The Tracker Icon has vanished from my taskbar. When I use Tracker via Accessories --> Tracker Search Tool, I get no results for any query.

TIA,
Tim

Go to System-Administration-System Monitor
Click on Processes
right click on trackerd and choose Kill process
open a terminal
type code : Trackerd -v 2 -R
this will reindex tracker.
when finished (it takes a while)
close terminal
go to Accessories-tracker search tool and right click on it
choose: add launcher to panel
Tracker should now be working.

Regards quibbler

---

### Post by haelen on 2008-05-12
Thanks quibbler.

This not only worked perfectly, but cured another problem I had with my system taking ages to save or open files.

It must have been directly related to the broken database or something.

Cheers,
Tim

---

### Post by hackerseraph on 2008-09-11
used lower case "trackerd -v 2 -R"

uppercase T on trackerd doesnt appear as a program; hope this helps anyone else who ran into case sensitivity issues

---

