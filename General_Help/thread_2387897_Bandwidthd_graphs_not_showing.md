---
title: "Bandwidthd graphs not showing"
date: 2018-03-25
forum: General Help
---

### Post by kete2018 on 2018-03-25
I have an OpenWRT-based router which provides bandwidthd probably as its best bandwidth monitor. There is not much info about configuring bandwidthd. When running bandwidthd on the router, it can make webpages with all of the information, but the processing is too much and causes the router to reboot.

I send bandwidthd data to a postgresql database on an Ubuntu server. I copied some bandwidthd PHP files for Apache, but the graphs don't appear. The webpages and the data does. I don't know how to figure out what's wrong.

I also tried ntop, but it didn't seem to provide as much information as bandwidthd; and its netflow collector requires a license. There might be another netflow importer, or Cacti might suffice.

---

