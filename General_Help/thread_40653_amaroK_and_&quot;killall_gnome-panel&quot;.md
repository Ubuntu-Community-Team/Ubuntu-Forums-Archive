---
title: "amaroK and &quot;killall gnome-panel&quot;"
date: 2005-06-09
forum: General Help
---

### Post by royg1234 on 2005-06-09
How do I switch to amaroK after a "sudo killall gnome-panel"?  I know I could just kill it and re-launch, but is there any other way to get back into it?  (clarification, I mean amaroK that runs in the tray)

---

### Post by Jussi Kukkonen on 2005-06-10
It's easier than you think - just relaunch it without killing it.

The amarok-wrapper checks if the real program (amarokapp) is already running, and just brings it to front if it is.

---

