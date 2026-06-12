---
title: "Editing Sessions via Failsafe Terminal?"
date: 2007-07-12
forum: General Help
---

### Post by schaefer on 2007-07-12
After installing compiz fusion and restarting, I was greeted with regular old metacity. So, I chose to put "compiz --replace" as a startup command in sessions. Now, when I try to log in, I am greeted by an organish colored background with a cursor, and no ability to do anything. Also, failsafe gnome does the exact same thing

I'm wondering how I would be able to remove the compiz comand through the failsafe terminal. Any commands or locations of the files to alter would be appreciated. I'm still a novice when it comes to linux, so any specific help would be great. Thanks.

---

### Post by sisco311 on 2007-07-12
```
rm /home/**your_user_name**/.config/autostart/*compizXXX.desktop*
```replace **your_user_name** with your user name and *compizXXX.desktop* with the proper file name

---

### Post by schaefer on 2007-07-12
Thanks a bunch sisco, that really did the trick! :)

---

