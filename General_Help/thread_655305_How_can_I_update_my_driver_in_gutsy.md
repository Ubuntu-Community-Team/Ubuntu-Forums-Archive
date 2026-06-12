---
title: "How can I update my driver in gutsy?"
date: 2008-01-01
forum: General Help
---

### Post by kris2pe on 2008-01-01
I tried downloading the latest envy but it doesn't seemed to work!
Where do I get the latest drivers?

---

### Post by taurus on 2008-01-01
Which nvidia card do you have and have you tried to install the restricted driver for your graphic card from System -> Administration -> Restricted Drivers Manager?

---

### Post by kris2pe on 2008-01-01
This is the error message! 
The software source for the package

   nvidia-glx-new

 is not enabled.

---

### Post by taurus on 2008-01-01
Go into System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and put a check mark on all the lines except the last one, Source code and the CDROM at the bottom window.  Close it and press Refresh.  Close synaptic window and see if you can install the nvidia driver for your graphic card now with System -> Administration -> Restricted Drivers Manager.

---

