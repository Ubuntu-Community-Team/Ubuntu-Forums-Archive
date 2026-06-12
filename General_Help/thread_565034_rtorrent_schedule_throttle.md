---
title: "rtorrent schedule throttle"
date: 2007-10-01
forum: General Help
---

### Post by fernando_lopes_jr on 2007-10-01
I added this line to my .rtorrent.rc sow I can control the program upload throttle but nothing happens when I start rtorrent It starts to upload with unlimited throttle can anyone give me a hand please to find whats wrong.

schedule = throttle_1,00:00:00,24:00:00,upload_rate=0
schedule = throttle_2,08:00:00,24:00:00,upload_rate=30

---

### Post by konsole on 2007-10-02
> **fernando_lopes_jr said:**
> I added this line to my .rtorrent.rc sow I can control the program upload throttle but nothing happens when I start rtorrent It starts to upload with unlimited throttle can anyone give me a hand please to find whats wrong.

schedule = throttle_1,00:00:00,24:00:00,upload_rate=0
schedule = throttle_2,08:00:00,24:00:00,upload_rate=30

When you start rtorrent it will use the upload_rate value in your .rtorrent.rc (0 if you haven't specified a value) UNTIL one of these scheduled times is reached and triggers a change to your upload rate by the schedule command.

---

### Post by fernando_lopes_jr on 2007-10-02
Ah ok thanks now I understand how it works

---

