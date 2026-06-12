---
title: "Update Manager launching itself @ start-up even though I disabled the feature"
date: 2014-02-04
forum: General Help
---

### Post by ns6TBHp on 2014-02-04
Thanks for taking a look at my issue...


I have noticed that for the last few days, for no reason I can think of, that the Update Manager has been opening itself when I boot into the OS. I have disabled it as a startup option so I am just not sure why it still starts. This was never an issue before. I find it really annoying that it starts up on its own and prefer to only use Update Manager on-demand. Can someone help me prevent it from auto starting? Thank you for your help..


I have already tried 

[LIST]
[*]Open the *Software Sources* application. 
[*]Select the "Updates" tab. 
[*]For the "Automatically check for updates" option, select **Never**. 
[/LIST]

the Update Manager still launches by itself at startup but then says it can't update unless I allow it. This did not solve the issue of it starting on its own.

---

### Post by ns6TBHp on 2014-02-05
if there is no solution to this probable bug, is it possible to like, delete the login account I am using and then create a new one that's all refreshed and default? Could this solve the issue, kinda like starting over? I prefer this over reinstalling the OS.

---

### Post by Dennis N on 2014-02-05
These are the things you did?

>     Open the Software Sources application.
    Select the "Updates" tab.
    For the "Automatically check for updates" option, select Never. 

Not clear: Did you disable the update notifier in **Settings > Session and Startup > Application Autostart** ?

---

### Post by ns6TBHp on 2014-02-05
yes that is the first thing i attempted. It still autostarts

---

### Post by Dennis N on 2014-02-06
In Software Sources > Updates
uncheck all boxes under "Install updates from"
and see if that prevents the notification.

---

