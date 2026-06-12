---
title: "Startup graphics process at login on desktop"
date: 2013-09-13
forum: General Help
---

### Post by eric22 on 2013-09-13
I have 2 processes that display and capture the output from cameras attached to an Ubuntu 12.04 box. When that box is powered on, it needs to run both of these programs. However, when I log into the system remotely to check on the data capture process (the usual method for accessing the machine), I do not want additional copies of the capture process spawned. Furthermore, the programs were both written such that they need to open up X-windows and display images. Does anybody have any ideas on how I can best accomplish this?

My original idea had been to set the process as a "Startup Application" and then just have the system auto-login to the right account, but this doesn't work. While the auto-login works fine, the autostartup link is not opening any programs. So, right now, I still have to startup the programs by hand at the actual computer.

Thank you in advance.
Eric

---

### Post by dcstar on 2013-09-17
> **eric22 said:**
> 
........While the auto-login works fine,** the autostartup link is not opening any programs**. So, right now, I still have to startup the programs by hand at the actual computer.


Then **you** have not created the correct link.

---

