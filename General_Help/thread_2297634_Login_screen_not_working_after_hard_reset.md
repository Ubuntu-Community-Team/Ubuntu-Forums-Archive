---
title: "Login screen not working after hard reset"
date: 2015-10-05
forum: General Help
---

### Post by peto1994 on 2015-10-05
Hi. Battery on my laptop runned out before it could auto-suspend.
After rebooting it shows normal ubuntu login screen for few moments, and then it only shows purple screen
and cursor. After few minutes of googling I found nothing. I tried to reinstall/reconfigure *lightdm* and *unity-greeter*
Also I ran fsck just to be sure. There are some errors in /var/log/lighten/x-0-greeter.log but I don't know if 
it will help. Please help, I don't know what else I should try. I'll try to upload those logs if it is needed.
EDIT: After combination of switching to CLI, switching to GUI, typing some commands and waiting login screen works as it should. After logout there is same problem - purple screen. At least I can login to GUI and I can type on notebook instead of phone.
Here is copy of */var/log/lightdm/x-0-greeter.log*. It looks like those messages starting after 200+ seconds were logged after it started to work.
[http://pastebin.com/raw.php?i=1fW5wLbp](http://pastebin.com/raw.php?i=1fW5wLbp)

---

