---
title: "Having problems with root Ubuntu 6.10"
date: 2006-11-06
forum: General Help
---

### Post by Mooseus on 2006-11-06
Hey everyone,
I'm having problems using root. I'm using Ubuntu 6.10. Whenever I try the sudo command to execute something which requires root privileges, I'm prompted with the pc asking for my password. In the terminal I can't seem to type my password - like it won't respond to any keys apart from enter. So I press enter and have to type the password quickly, as it seems there's a timer or something. After typing my password, it believes that I don't have to correct one. I recall exactly what that password was which I first entered. Is there a way of changing passwords? I tried doing it in the User and Groups application and changing the properties of root, but it won't change the password. It will allow me to type another one, but when I reload the properties screen, it's been changed back to what it was before.

The strange thing is when I'm not in the terminal and type my password when prompted (to do things as root) it works fine.

Thanks in advance,

---

### Post by po0f on 2006-11-06
Mooseus,

When you type `sudo command`, it asks for *your* password, not root's.  Just enter your password.  And it doesn't echo the password or *'s to the screen, but it is still reading your password as you type it.  Don't make a typo.  ;)

---

### Post by aysiu on 2006-11-06
Sounds as if it's [this problem](http://ubuntuforums.org/showthread.php?t=214393&highlight=feedback+terminal).

---

