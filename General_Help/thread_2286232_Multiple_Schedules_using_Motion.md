---
title: "Multiple Schedules using Motion"
date: 2015-07-10
forum: General Help
---

### Post by Darrell_Atkinson on 2015-07-10
Not sure if anyone has done this, but it's worth a shot. I am using Motion to manage my IP cameras for home surveillance. Right now all cameras are on a single schedule controlled by cron. I'd like to be able to setup schedules individually for each camera, has anyone done this, or perhaps know how or if it is possible with Motion? The constraint I see is that when Motion is running it reads the motion.conf file and that references the threadx.conf files required for each individual camera. So whenever I start Motion, every camera also starts capturing, (or at least "talking" across my network, they only capture if motion is detected).

---

