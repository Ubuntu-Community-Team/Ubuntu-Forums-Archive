---
title: "update glitch"
date: 2012-11-06
forum: General Help
---

### Post by aspergerian on 2012-11-06
For several days, update has been generating a message new to me (see two screen shots). When message first appeared, 17 updates were available and seemed to update correctly. My internet seems to be working fine on this Acer 1410 (64 bit; 4g ram) and on my win7 HP. Suggestions appreciated.

---

### Post by JKyleOKC on 2012-11-06
It's possible that the "redshift-ppa" is no longer available; that's the only source mentioned in the error message. Depending on the specific version you're using (Ubuntu, Xubuntu, Lubuntu, Kubuntu, and so on) you may have a different way of controlling your repository list, but if you have Synaptic package manager available you can use its Settings>Repositories menu choice to adjust it. Find the three lines mentioned in the error message and remove the tick from the checkbox for each of them. That should remove them while leaving them available to be activated again if need be...

On the Xubuntu 10.04.4 of this machine, there's a choice for "Software Sources" in the settings menu that you can use. The same list is used for all of the update/download actions so either place will have the same effect.

---

### Post by ibjsb4 on 2012-11-06
The last release of redshift-ppa was for 10.10

So your out of luck for 12o4; remove it or just uncheck it in software sources.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)

---

### Post by aspergerian on 2012-11-07
Suggestions by Jim Kyle and ibjsb4 were helpful; thank you.

I removed items related to redshift via directions at [https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)

Retested check updates. The problem has disappeared.

---

### Post by ibjsb4 on 2012-11-07
You may also be interested in ppa-purge for future use.

[http://packages.ubuntu.com/lucid-backports/ppa-purge](http://packages.ubuntu.com/lucid-backports/ppa-purge)

---

