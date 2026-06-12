---
title: "Tracker file search broken (with error message) on Gutsy"
date: 2008-03-09
forum: General Help
---

### Post by breaking on 2008-03-09
When I try to run a search with the Tracker Search Tool, an error box pops up saying "The following error has occurred: Process /usr/bin/trackerd exited with status 0". Clicking OK, the error disappears and I'm sent back to the search screen, which is still empty. 
This happens regardless if I'm trying to search from Nautilus or the Tracker Search Tool directly. 

**More info that might be useful:**
If I type ```
killall trackerd
```
and ```
/usr/bin/trackerd
```
it answers with```

Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0

```
if I tell it to start /usr/bin/trackerd without the killall first, I get that same preamble with:
```
 ** WARNING **: Tracker daemon is already running - exiting
```
at the end.
How can I fix it?

---

### Post by breaking on 2008-03-11
how much is bumping frowned upon in these forums?
this is still a problem.

---

### Post by ryanhaigh on 2008-03-16
If you are not interested in using tracker then you may be insterested in my [howto on recompiling nautilus without tracker integration.]("http://ubuntuforums.org/showthread.php?p=4524368")

---

