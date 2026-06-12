---
title: "Root terminal commands cant open window by default, how change?"
date: 2018-01-27
forum: General Help
---

### Post by grandkodiak2 on 2018-01-27
So I'm having problems getting any root or sudo command that opens a GUI (like leafpad or gparted) to run unless I type
xhost +SI:localuser:root

after a reboot however I have to run that command again to fix the problem. how can i make this a permanent change?

---

### Post by deadflowr on 2018-01-27
Create a Startup Application for it.
(Open Startup Applications, click on Add give it a name, and paste the command into the command field and save/click Ok)

---

### Post by grandkodiak2 on 2018-01-27
thanks, figured it was a script to be added somewhere, didnt know it would be that easy lol

---

