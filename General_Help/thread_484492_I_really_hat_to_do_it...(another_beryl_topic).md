---
title: "I really hat to do it...(another beryl topic)"
date: 2007-06-25
forum: General Help
---

### Post by lock, stock and linux on 2007-06-25
but i cant find anything

i have used these instructions on how to get beryl and xgl on my amd64 using fiesty

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI")

it was all fine but the last step------------------------------

 Missing Icons in Shutdown Menu Fix

Your /usr/bin/startxgl.sh should look like this:

#!/bin/sh
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4 
export DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session

----------------------------
i did all that but all i see is a black screen with a white x as my mouse 
i can still move to my other 3 workspaces witch work fine 

any help appresiated

EDIT:when i right click on my beryl icon and click "select window manager" it is checked on "metacity"
i tried putting ot on beryl and my screen flashed and went back to metacity

---

