---
title: "Unable to modify time and date (Precise unity desktop)"
date: 2012-12-13
forum: General Help
---

### Post by windofkeltia on 2012-12-13
a) I can see the time in the top panel.
b) Clicking and choosing Time & Date Settings reveals correct Location.

Set the time: O Automatically
--this simply shows the wrong time (about 6 hours behind)

Set the time: O Manually
--I can change the time, but it does not stick: it ignores me.

This is too annoying as I depend on file dates and times which are now nonsense.

Profuse thanks for any help.

---

### Post by pierceTN on 2012-12-13
> **windofkeltia said:**
> a) I can see the time in the top panel.
b) Clicking and choosing Time & Date Settings reveals correct Location.

Set the time: O Automatically
--this simply shows the wrong time (about 6 hours behind)

Set the time: O Manually
--I can change the time, but it does not stick: it ignores me.

This is too annoying as I depend on file dates and times which are now nonsense.

Profuse thanks for any help.

does it have an unlock button on the top of the window?


Pierce

---

### Post by windofkeltia on 2012-12-13
No, there's no control I can see.

---

### Post by Rexilion on 2012-12-14
These are of the most undocumented annoyances in Linux. Therefore I have a file for this containing the commands to (correctly) set the system clock.

```
LC_ALL=C date
```
Get your current date as provided by the system. Adjust it's output to the correct date. And fill this in below after the --set="". Make sure to keep the "-signs intact!

```
sudo date --set="Sat Aug 25 11:41:19 CEST 2012"
```
Substitute and run.

```
sudo hwclock --systohc --utc
```
Copy systemclock to the hardwareclock.

And finally reboot.

---

