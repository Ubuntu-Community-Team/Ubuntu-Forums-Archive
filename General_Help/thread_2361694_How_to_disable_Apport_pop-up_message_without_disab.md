---
title: "How to disable Apport pop-up message without disabling Apport?"
date: 2017-05-19
forum: General Help
---

### Post by ahajdu2 on 2017-05-19
[COLOR=#111111][FONT=Ubuntu]Is there a way to disable the Apport pop-up dialog error message that appears when an Ubuntu error occurs **without** disabling Apport?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Message that appears in the pop-up: "Sorry, Ubuntu 16.04 has experienced an internal error."[/FONT][/COLOR]

---

### Post by deadflowr on 2017-05-19
Open a terminal and try running
```
gsettings set com.ubuntu.update-notifier show-apport-crashes false
```
from here:
[https://wiki.ubuntu.com/Apport]("https://wiki.ubuntu.com/Apport")

---

