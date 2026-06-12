---
title: "Undoing a recent update"
date: 2012-12-12
forum: General Help
---

### Post by aandrews on 2012-12-12
Earlier today (I think!) I OK'd a bundle of updates and now the "switcher", which previously allowed applications to be dragged to another workspace tab, is messed up.  Previously the same desktop contents was reflected on each workspace.  Now the others are devoid of anything. 

How can I un-do a recent update?  And if not, is there documentation associated with the release of general bundled updates that are done periodically?  In other words, can I at least find out what was done to screw up my desktop so?

---

### Post by Ms. Daisy on 2012-12-13
You can use synaptic package manager. If you look under "File" then "History" you'll see what you installed today.  Then you could remove each update to see which resolves the problem.

---

### Post by mc4man on 2012-12-13
> **Ms. Daisy said:**
> You can use synaptic package manager. If you look under "File" then "History" you'll see what you installed today.  Then you could remove each update to see which resolves the problem.
I believe Synaptic only keeps a history of packages installed thru synaptic, one of the good reasons to use it instead of cli or software-updater
> **aandrews said:**
> Earlier today (I think!) I OK'd a bundle of updates and now the "switcher", which previously allowed applications to be dragged to another workspace tab, is messed up.  Previously the same desktop contents was reflected on each workspace.  Now the others are devoid of anything. 

How can I un-do a recent update?  And if not, is there documentation associated with the release of general bundled updates that are done periodically?  In other words, can I at least find out what was done to screw up my desktop so?

You may want to note what ubuntu release & what session you are using & solve your issue rather than try to backtrack updates
(unless you used synaptic it can be a little bit of a chore to find - you could run this in a terminal & likely figure out based on date & time
```
cat /var/log/dpkg.log | grep 'status installed'
```

---

### Post by Ms. Daisy on 2012-12-14
> **mc4man said:**
> I believe Synaptic only keeps a history of packages installed thru synaptic
Aha- I didn't know that!

---

### Post by haqking on 2012-12-14
doesnt 

```
cat /var/log/apt/history.log
``` store it also ? I dont have access to a apt based machine right now to check though

---

### Post by Ms. Daisy on 2012-12-14
> **haqking said:**
> doesnt 

```
cat /var/log/apt/history.log
``` store it also ? I dont have access to a apt based machine right now to check though
It does indeed.

---

