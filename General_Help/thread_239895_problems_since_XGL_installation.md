---
title: "problems since XGL installation"
date: 2006-08-20
forum: General Help
---

### Post by justin2021 on 2006-08-20
ever since i installed xgl a couple of days ago, i've been having some problems. one of them is that xine's control panel no longer works, and it lookes all messed up. the other problem is that on gaim, when i backspace and type words to fast, it restarts x. is there any way to fix this stuff?:confused: :confused: :confused:

---

### Post by kpkeerthi on 2006-08-20
For the xine problem, a screenshot may help.
Try [http://www.compiz.net/topic-1199-solved-shift-backspace-crashes-compiz](http://www.compiz.net/topic-1199-solved-shift-backspace-crashes-compiz) to fix the backspace issue.

---

### Post by justin2021 on 2006-08-20
Ok, think i fixed the xgl problem. here is a pic of the xine windows opened. 


[IMG]http://i80.photobucket.com/albums/j168/justin2021/messedupxine.png[/IMG]

---

### Post by kpkeerthi on 2006-08-20
Ah... I had the same issue with gxine when running Xgl. I could not get it fixed. I switched over to totem-xine. Pretty neat now.

---

### Post by Fac51 on 2006-08-20
that's that key icon on your desktop??

---

### Post by justin2021 on 2006-08-20
"that's that key icon on your desktop??"

yeah its just some icon i found and am using to start up XGL

Whenever i put in this command:

xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

does it only work untill i turn of the computer? because after i turned it off and turned it back on later, it was doing the shift+backspace error again, and restarting x. do i have to input this command everytime i do xgl?:(

---

### Post by kpkeerthi on 2006-08-20
Add the command to your compiz startup script file.

---

### Post by Fac51 on 2006-08-23
> **justin2021 said:**
> "that's that key icon on your desktop??"

yeah its just some icon i found and am using to start up XGL


i want the key, can you post it for me?
please and thank you

---

