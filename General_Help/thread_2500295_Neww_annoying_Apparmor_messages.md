---
title: "Neww annoying Apparmor messages"
date: 2024-08-29
forum: General Help
---

### Post by georgesgiralt on 2024-08-29
Hello Guys,
Since a couple of days, I've got annoying apparmor messages popping up on my screen all the time. See attached picture. Previously, I had the same amount of apparmor messages but they went to the system log files and not showed up on my screen.
I wonder why it is so and how I can suppress them in order not to pop up anymore ? 
I can't remember a change (except for software updates) which could lead to such behaviour. 
My system is running 22.04.4 LTS and is up to date Ubuntu wise.
Thank you in advance for your help !
Have a nice and bright day !
[IMG]https://i19.servimg.com/u/f19/17/79/70/72/captur47.png[/IMG]

---

### Post by georgesgiralt on 2024-09-02
Hello,
I reply myself to my question because I've found the problem and cured it. 
It was caused by the package apparmor-notify which was installed as a companion to other software. 
Once purged, messages disappeared.
Maybe this will serve others.
Have a nice and bright day.

---

