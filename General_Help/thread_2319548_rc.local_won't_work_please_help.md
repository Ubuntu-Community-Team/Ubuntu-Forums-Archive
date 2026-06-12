---
title: "rc.local won't work please help"
date: 2016-04-05
forum: General Help
---

### Post by zap199x on 2016-04-05
i used :
cd /etc 
sudo vim rc.local
and used vim to add this line to it , but for some reasons when i restart my computer the command doesn't get executed at all.

---

### Post by ajgreeny on 2016-04-05
Please do not add large inline images as some users may not even bother to look at the post if they have a slow dial-up connection.  Please use the attachment icon in the toolbar (a paperclip) which adds a thumbnail linked to a larger image.

To your problem.
Does that command ```
xinput set-prop 8 274 8
``` work for you when you use it in terminal?

Does it have to be run as root, which is how rc.local will run it, so whatever changes it makes to xinput may be valid for root user only, not for you as user.

If that command runs in terminal without sudo, as user, you should run it by using a script added to your autostart applications, not put it in rc.local.

---

### Post by zap199x on 2016-04-05
ty for quick answer ... sorry i have never use such forums before .... i'll try putting it into startup application ty , it doesn't need sudo to work but i thought its ok to just put it there -.-

---

### Post by ajgreeny on 2016-04-06
I have edited your post and changed the large image to an attached image with thumbnail showing.

I have no idea what that xinput command does never having needed to use xinput so far, but instead of using rc.local add an executable script to your home with following content and see if it works.  Another reason that it may not work when run from rc.local is that the xsession is not running at that point in startup.
```
#!/bin/bash
sleep 10; xinput set-prop 8 274 8
``` Save it as xinput.sh and make executable with ```
chmod +x xinput.sh
```
The sleep 10 may not be needed but I've added it at this stage just to be certain that the xsession running properly; try it without if you like.

---

