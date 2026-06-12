---
title: "Browser tearing when scrolling"
date: 2018-01-03
forum: General Help
---

### Post by mcswiggans on 2018-01-03
Hi I recently installed Xubuntu 16.04 and am having problems getting browsers to work. I tried using firefox but there was flickering/tearing in horizontal bands across the screen and none of the solutions (turning off hardware acceleration, restarting in safe mode).
I tried installing chrome but it caused a problem where whenever I tried dragging any windows across the screen they would stutter and lag. I fixed this by disabling hardware acceleration but now I have the same problem I did with firefox. I tried enabling GPU rasterization in chrome://flags but that does not work.
I am using nvidia driver v384 w/ compton and have a GTX 1060 installed.

---

### Post by Autodave on 2018-01-04
Where did you get the 384 driver from?

---

### Post by walts48 on 2018-01-04
Did you try disabling Smooth Scrolling in Firefox? 

Preferences > General and scroll down to the Browsing heading.

---

### Post by mcswiggans on 2018-01-04
Thanks, disabling smooth scrolling solved it

---

### Post by RobGoss on 2018-01-04
You can mark this thread as solved if you resolved your issue. Thank you for sharing your fix with the forum

---

