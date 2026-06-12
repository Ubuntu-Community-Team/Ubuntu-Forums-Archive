---
title: "Ubuntu Software App vs Software Updater App"
date: 2016-07-17
forum: General Help
---

### Post by Incarnadine on 2016-07-17
I checked for available updates in the Ubuntu Software app and then out of curiosity checked for updates using the Software Updater app, and the updates were different. How is this possible? Shouldn't the available updates be the same in both apps?

I know, I should have taken a screen shot and attached it to this thread, but I wasn't thinking at the time and decided to run the updates using the Software Updater app. Once I did this, the available updates in the Ubuntu Software app disappeared, but they were definitely not the same updates. The title of the updates were completely different. :confused:

---

### Post by deadflowr on 2016-07-17
Software Updater, or update-manager uses the phased-updates function.
Ubuntu Software > Updates, does not.
See here:
[https://wiki.ubuntu.com/PhasedUpdates]("https://wiki.ubuntu.com/PhasedUpdates")

Ubuntu Software will show the same packages as running the command line: apt-get upgrade, though.

---

### Post by Incarnadine on 2016-07-17
> **deadflowr said:**
> Software Updater, or update-manager uses the phased-updates function.
Ubuntu Software > Updates, does not.
See here:
[https://wiki.ubuntu.com/PhasedUpdates]("https://wiki.ubuntu.com/PhasedUpdates")

Ubuntu Software will show the same packages as running the command line: apt-get upgrade, though.

Wow, super helpful. Thanks a bunch! :popcorn:

---

