---
title: "can I disable ofono and  dundee services?"
date: 2023-07-12
forum: General Help
---

### Post by bjlockie on 2023-07-12
can I disable ofono and  dundee services?
I want to trim 0.02s off my boot time by getting rid of them. :-)

---

### Post by Rubi1200 on 2023-07-13
I'm not sure I understand the point of trying to shave 0.02s off boot time.

You can use systemd-analyze to view boot times and systemctl to start, stop, disable services.

---

### Post by bjlockie on 2023-07-13
Is it safe to disable dundee and ofono?

---

### Post by Rubi1200 on 2023-07-14
It's really not for me to say. You know what programs are installed and which services are running. However...based on what I could find I would say it should be okay to disable them.

---

