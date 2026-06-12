---
title: "Supress Updates?"
date: 2006-07-16
forum: General Help
---

### Post by krazykirk on 2006-07-16
Hi Everyone, Is there any way that i can supress updates from the update manager? I currently use the 686 kernel, but my old 386 kernel still wants to be updated. I'm not planning to update, so i keep unticking it as i upgrade everything, but this is getting annoying.

Any help anyone?

---

### Post by Titus A Duxass on 2006-07-16
Edit /etc/apt/sources.list and comment out all the lines with a #.

This can done through a GUI also, but I don't know how. Probably one of the advanced options in the apt manager.

---

### Post by aysiu on 2006-07-16
Go to Synaptic Package Manager and go to Package > Lock Version.

---

### Post by krazykirk on 2006-07-16
Thanks! Worked like a charm

---

