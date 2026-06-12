---
title: "cannot remove startup apps!"
date: 2008-06-04
forum: General Help
---

### Post by DesiDishoom on 2008-06-04
every time i log in to a new session, a pidgin window and a terminal window open up, slowing down startup time and just looking ugly...kinda 

i tried looking in the Session Preference, and i couldn't find either of them in the list of starup programs, and i don't have the "Automatically remember running applications" option checked either...

is there a way other than the session preferences dialog to modify startup programs?? i would greatly really appreciate any help!! i'm using hardy 8.04, btw.

---

### Post by DesiDishoom on 2008-06-05
anybody?

---

### Post by Kernel_Krunch on 2008-06-05
> **DesiDishoom said:**
> anybody?

Check your /etc/rc.local

if not then check out /etc/init.d  it has every startup script

---

### Post by Keith Hedger on 2008-06-05
shut everything down so u just have your desktop and go to preferences->sessions->session options and hit "remember  current apps" that should get rid rid of them, ive had similar problems before

---

### Post by DesiDishoom on 2008-06-05
> **Keith Hedger said:**
> shut everything down so u just have your desktop and go to preferences->sessions->session options and hit "remember  current apps" that should get rid rid of them, ive had similar problems before
good call, that worked! don't know why i didn't think of that...

---

### Post by run1206 on 2008-06-06
thanks Kernel & Keith.  I saved sessions with all apps off (including boinc_client) as well as edited its script to not run during startup from the init.d files.  startup's much quicker now :D

---

