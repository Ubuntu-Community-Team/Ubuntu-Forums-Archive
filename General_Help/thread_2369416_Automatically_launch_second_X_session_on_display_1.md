---
title: "Automatically launch second X session on display :1 at boot"
date: 2017-08-22
forum: General Help
---

### Post by utahul1 on 2017-08-22
Simple question, but I'm having a hard time finding a straight answer. I have a stock Ubuntu 16.04 LTS desktop install, and when I finally see the login screen (lightdm) at the end of the boot process, I can drop to a tty, login as a non-root user (let's call it 'user1') and then start a second X session on vt8 with the command ```
startx -- :1 vt8
```. It works as expected and launches Unity on vt8. Well... what I'd like to do is automate that process so that when the machine boots, it automatically launches that second X session on vt8 as user1 without any actual user intervention. Additionally, I need x11vnc to launch immediately thereafter to make the X session available remotely (x11vnc is easy to set up -- the question is more about how/where to best invoke x11vnc once the second X session is automatically launching on display :1).

I've tried using the hooks feature as mentioned in the lightdm.conf file, but I couldn't get it to work -- maybe I didn't set it up right. Any thoughts, hints, suggestions, etc would be appreciated.

Thanks all!

---

