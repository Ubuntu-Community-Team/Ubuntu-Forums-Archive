---
title: "Time wasting command?"
date: 2007-01-23
forum: General Help
---

### Post by peanut butter on 2007-01-23
hi, i am making a shell script to use pport to turn something on then off through the paralell port. I would like to set the port to on, then 30 seconds later turn the device off. how would i accomplish this?

---

### Post by inCursorated on 2007-01-23
using bash...

sleep 30s     # wait for 30 seconds

---

### Post by ciscosurfer on 2007-01-23
> **inCursorated said:**
> using bash...

sleep 30s     # wait for 30 secondsThe 's' is unnecessary.  **sleep 30** will do the job.

---

