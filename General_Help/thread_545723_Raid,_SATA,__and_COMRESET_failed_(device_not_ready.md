---
title: "Raid, SATA,  and COMRESET failed (device not ready)"
date: 2007-09-07
forum: General Help
---

### Post by glave on 2007-09-07
I'm staring at the end of a 2 month long ordeal with a raid setup and I'm desperate for help. 

In June I decided to add more space to my server. I've been running a raid5 array w/ 4 300g sata drives off a promise card for well over a year and a half with ZERO problems. I was also using Edgy. My server had another promise card in it, so I purchased 4 500g hds and hooked them up to it. I had also upgraded to Feisty. Then the problems began....

As I started moving data over and filling up the new drives (I was using LVM to group them all together), I started getting "COMRESET failed (device not ready)" errors in kern.log, and drives would drop out of my array. I thought I had bad hard drives, so I've replaced them. In a nutshell, this is a rundown of everything I've checked:

[LIST]
[*]Did a long disk check of the harddrives using seagate's boot cd testing tool.
[*]Replaced any drive that had any kind of sector errors
[*]Split the drives onto multiple power cables direct from the power supply instead of daisy chaining
[*]Replaced all sata cables
[*]Replaced the sata controller card that controls the 500g drives (both cards are promise)
[/LIST]

Anytime I start moving big data around on the 500g I get problems. Resyncing the array can cause it. I've read that kernel 2.6.19 could have possible problems with sata timeouts, but I only saw 1 post referencing this, and no solution. Does anyone know if Edgy was more stable with sata and raid? Any ideas on a cause or direction of a solution? 

Two months and I've not got this solved, and I've lost a good amount of data twice over the course of it. :(

---

### Post by glave on 2007-09-08
anyone?

---

