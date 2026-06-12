---
title: "Maps problem"
date: 2021-06-08
forum: General Help
---

### Post by Panawe on 2021-06-08
A nice little program I use based on the OSM database has suddenly stopped launching. Can anyone suggest a solution?

TIA

---

### Post by QIII on 2021-06-08
Would you please attempt to launch it from the command line and provide the resulting messages?

---

### Post by Panawe on 2021-06-08
From Terminal if I type in "Maps" it says "command not found"

---

### Post by dragonfly41 on 2021-06-08
Try "maptool"

---

### Post by Panawe on 2021-06-08
From Terminal:

Command 'maptool' not found, but can be installed with:

sudo apt install maptool

---

### Post by dragonfly41 on 2021-06-08
If you use Synaptic Package Manager, simply search "maptool", visit website
you are taken here .. [https://www.navit-project.org/](https://www.navit-project.org/)

and so I would just follow advice
sudo apt install maptool
or install via Synaptic Package Manager

---

### Post by Panawe on 2021-06-08
Thanks.
Done that but when I type "maptool" in terminal it asks me to specify an output file.

---

### Post by Panawe on 2021-06-08
Okay, here goes:

> maptool maps
PROGRESS: Phase 1: reading input data 0:00 0 MB
PROGRESS1: Processed 0 nodes (0 out) 0 ways 0 relations 0 tiles 0:00 0 MB
PROGRESS1: Processed 0 nodes (0 out) 0 ways 0 relations 0 tiles 0:30 0 MB
PROGRESS1: Processed 0 nodes (0 out) 0 ways 0 relations 0 tiles 1:00 0 MB
PROGRESS1: Processed 0 nodes (0 out) 0 ways 0 relations 0 tiles 1:30 0 MB
PROGRESS1: Processed 0 nodes (0 out) 0 ways 0 relations 0 tiles 2:00 0 MB
PROGRESS1: Processed 0 nodes (0 out) 0 ways 0 relations 0 tiles 2:30 0 MB
PROGRESS1: Processed 0 nodes (0 out) 0 ways 0 relations 0 tiles 3:00 0 MB
PROGRESS1: Processed 0 nodes (0 out) 0 ways 0 relations 0 tiles 3:30 0 MB
PROGRESS1: Processed 0 nodes (0 out) 0 ways 0 relations 0 tiles 4:00 0 MB
PROGRESS1: Processed 0 nodes (0 out) 0 ways 0 relations 0 tiles 4:30 0 MB
PROGRESS1: Processed 0 nodes (0 out) 0 ways 0 relations 0 tiles 5:00 0 MB
PROGRESS1: Processed 0 nodes (0 out) 0 ways 0 relations 0 tiles 5:30 0 MB
PROGRESS1: Processed 0 nodes (0 out) 0 ways 0 relations 0 tiles 6:00 0 MB
PROGRESS1: Processed 0 nodes (0 out) 0 ways 0 relations 0 tiles 6:30 0 MB
PROGRESS1: Processed 0 nodes (0 out) 0 ways 0 relations 0 tiles 7:00 0 MB

Just seems to be endless iterations.

---

### Post by dragonfly41 on 2021-06-08
I pass from this point on ... all I did was point it out.  It does refer to OSM database as in your opening question.
Try maptool --help.

---

