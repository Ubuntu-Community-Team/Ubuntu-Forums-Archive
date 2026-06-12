---
title: "Multiple ubuntu machines crashing simultaneously.."
date: 2017-12-15
forum: General Help
---

### Post by minewealth on 2017-12-15
Currently in a dilemma.. we currently have about 6 machines running 16.04 desktop, each of them have identical hardware and each of them has been cloned using clonezilla from a master hard disk template. The ip address is set manually on the router side by binding individual mac address from each machine to a specific ip, apart from that no changes was done on the machine from our side

Works fines for a few hours, however, suddenly ALL but one (sometimes none) of them will fail to respond to pings or ssh attempts, according to our logs (each machine makes a curl request to our external http server each minute), all of them stop transmitting at nearly exactly the same minute, it is too coincidental for 6 machines to fail exactly at the same time

At first we thought the switch connecting all of them together was having issues, so we connected one of them machines directly to our router, and it still went down together with the rest (also, we are using a mix of cat5 and cat 6 cables, if it makes a difference), our ip camera is working and is on the same network so its not a network issue

The machines are in a off-site location so it would take a few hours to get someone to manually reset all the machines, this is the second time it has occurred, manually resetting them is the only way to get them back online

What could be the possible causes for them going down and where should I look to trace the issue? (eg, logs etc) I've got a feeling its something elementary that was not configured properly and causing all them to crash

Hoping somebody can help as I'm still quite new to ubuntu.. cheers!

Ok an update, it seems that the switch connecting 5 of the machines may have a problems, I found out that all of them are still functioning, but no longer get have network connections..

But the one that is connected directly to the router that bypasses the switch works flawlessly until now

We have replaced the switch 3 times with 3 different models, what wcould be the issue?

---

### Post by strixtux on 2017-12-16
Identical machines with identical software setup bar the IP address. There must be another reference which is still identical and should not be.

---

