---
title: "Recover password?"
date: 2008-05-30
forum: General Help
---

### Post by richard1224 on 2008-05-30
I just recently updated from 7.10 to 8.04 using an alternate CD. However, the new version now requires me to enter my password to load 8.04. I have not used my password since installing 7.10 and have "lost" it since then. Does anyone have any idea how I can recover this password or will I now have no choice but to reinstall 8.04 from scratch? I guess that I would have to format the ext partition first?   Thanks.

---

### Post by thefunnyman on 2008-05-30
[This]("http://ubuntuforums.org/showthread.php?t=142110") might help....

---

### Post by aysiu on 2008-05-30
Try these instructions:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by richard1224 on 2008-05-30
> **aysiu said:**
> Try these instructions:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Thanks for your suggestion. I entered the 'root' mode, changed my password, it was accepted. It looked perfect except when I logged in again to 8.04 it keeps asking for the username/password. If you have any other thoughts I would appreciate it.

---

### Post by aysiu on 2008-05-30
> **richard1224 said:**
> Thanks for your suggestion. I entered the 'root' mode, changed my password, it was accepted. It looked perfect except when I logged in again to 8.04 it keeps asking for the username/password. If you have any other thoughts I would appreciate it.
Well, resetting the password doesn't stop you being prompted for a username and password. It just makes sure that you know what the password is that you're supposed to enter when prompted.

---

### Post by richard1224 on 2008-05-30
> **aysiu said:**
> Well, resetting the password doesn't stop you being prompted for a username and password. It just makes sure that you know what the password is that you're supposed to enter when prompted.

I'm sorry, I didn't make my comment very clear. The problem is that I am not logged in even with my new password - it just cycles back to the login page again instead of actually loading 8.04.

---

### Post by aysiu on 2008-05-30
> **richard1224 said:**
> I'm sorry, I didn't make my comment very clear. The problem is that I am not logged in even with my new password - it just cycles back to the login page again instead of actually loading 8.04.
Are you able to log in at the terminal?

Press Control-Alt-F1 and this should take you to a full-screen terminal. Then try to log in with your username and password.

---

### Post by richard1224 on 2008-05-30
> **aysiu said:**
> Are you able to log in at the terminal?

Press Control-Alt-F1 and this should take you to a full-screen terminal. Then try to log in with your username and password.

Good idea - but when? First I get the Grub menu, no terminal.
Then I get the blank log in screen, no terminal. I don't think that I am getting far enough to try that.

---

### Post by aysiu on 2008-05-30
If you press Control-Alt-F1 whenever you get the blank screen, that should at least give you an idea of what part of the process things are freezing up during?

From your earlier post, it seemed as you were able to get to the login screen, though.

---

### Post by anaconda on 2008-05-30
try to boot to the text mode, and then type startx to start the graphical session.

If it works then you might be able to correct your settings  (or atleast make ubuntu login without asking password,,)from:
system>administration>login window

---

### Post by richard1224 on 2008-05-30
> **aysiu said:**
> If you press Control-Alt-F1 whenever you get the blank screen, that should at least give you an idea of what part of the process things are freezing up during?

From your earlier post, it seemed as you were able to get to the login screen, though.

Well, its the only log in screen that I've seen since installing 7.10. It's a plain colored screen with the Ubuntu logo and the log in window(s). I set up my preferences from the start (7.10)to use the automatic login and never have seen any other style.The automatic feature was lost when I upgraded to 8.04. Thats when I "lost" my password when asked for it. Maybe I still will need to reinstall 8.04 from the beginning? I don't know why it won't recognize the new password and load the system - it just cycles back again to ask for the same user/passwd.

---

### Post by aysiu on 2008-05-30
So what I'm saying is - when you get to the login screen that keeps looping, at that point, press Control-Alt-F1 and try to log in through the fullscreen terminal.

---

### Post by richard1224 on 2008-05-30
> **aysiu said:**
> So what I'm saying is - when you get to the login screen that keeps looping, at that point, press Control-Alt-F1 and try to log in through the fullscreen terminal.

MANY thanks for your interest and help. I load 8.04 from the grub menu. Then I get the Ubuntu colored screen and musical note. At the login screen I try the cnt-alt-F1 and get a complete screen lockup.  Cnt-alt-del gets me back to the grub menu. Can you believe this?

---

### Post by aysiu on 2008-05-30
The screen lockup is bizarre.

Control-Alt-Delete makes sense, though, as that reboots the computer.

---

