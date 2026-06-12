---
title: "disable a particular update"
date: 2008-01-22
forum: General Help
---

### Post by survient on 2008-01-22
I'm not trying to disable update-notifier(actually I'd like a notification applet that notifies me of my other network machines running ubuntu when they have updates on my main box), just a particular update that pops up(bluez-utils(I had to make a custom version to enable some features, so I can't update it otherwise it will overwrite the changes)). Is there a way to disable just that one update?

---

### Post by mcduck on 2008-01-22
Open the Synaptic Package Manager, find the bluez-utils package, select it and go to Package/Lock Version. Now that package won't be updated unless you remove the lock.

---

### Post by zvacet on 2008-01-22
Yes it is.Go to the synaptic,mark package you don´t want to update>**package>lock version**.

---

### Post by survient on 2008-01-22
Thanks guys.

---

