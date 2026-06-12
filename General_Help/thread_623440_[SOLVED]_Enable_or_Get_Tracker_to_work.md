---
title: "[SOLVED] Enable or Get Tracker to work"
date: 2007-11-25
forum: General Help
---

### Post by 1337455 10534 on 2007-11-25
Several threads on this before, and I've tried and not-liked Beagle that much before, how do I get tracker to work?  I installed libtrackerclient-dev tracker-utils tracker-search-tool but still no go.

---

### Post by 1337455 10534 on 2007-11-25
So, I;
```

sudo apt-get remove tracker-search-tool
sudo apt-get install libtrackerclient-dev tracker-utils tracker-search-tool

```
then I;
```

family@Purple-Blanket:~$ trackerd v


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Throttle level is 0
ERROR: execution of prepared query InsertWatch failed due to constraint failed with return code 19
ERROR: execution of prepared query InsertWatch failed due to constraint failed with return code 19
ERROR: execution of prepared query InsertWatch failed due to constraint failed with return code 19
ERROR: execution of prepared query InsertWatch failed due to constraint failed with return code 19
ERROR: execution of prepared query InsertWatch failed due to constraint failed with return code 19
ERROR: execution of prepared query InsertWatch failed due to constraint failed with return code 19

```
Error 19s still coming on strong, not working still..

---

### Post by 1337455 10534 on 2007-11-25
Now I'm getting;
```

** (trackerd:8639): CRITICAL **: tracker_indexer_get_hits: assertion `query->words' failed

** (trackerd:8639): CRITICAL **: tracker_indexer_get_hits: assertion `query->words' failed

```

---

### Post by 1337455 10534 on 2007-11-25
```

tracker-status

```
shows that it is indexing... =p

Yay1 It works now!!

---

### Post by fjgaude on 2007-11-25
I've noticed that Tracker takes several hours to index words before it shows any results from a search.

---

