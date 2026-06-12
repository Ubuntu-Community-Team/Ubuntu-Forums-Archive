---
title: "Fast User Switching"
date: 2006-12-06
forum: General Help
---

### Post by justin on 2006-12-06
Here's my dilemma. I enjoy using simple window managers such as fluxbox and pekwm, and I have another user on the computer who wouldn't let me run linux if it wasn't for the ease of use of gnome. 

Is it possible for me to get back to the gdm so the other user can log in, check their email, and log out, without my pekwm session being logged out?

---

### Post by dcstar on 2006-12-06
> **justin said:**
> Here's my dilemma. I enjoy using simple window managers such as fluxbox and pekwm, and I have another user on the computer who wouldn't let me run linux if it wasn't for the ease of use of gnome. 

Is it possible for me to get back to the gdm so the other user can log in, check their email, and log out, without my pekwm session being logged out?

The facility for additional simultaneous logins is built in Gnome, do a forum search and you should find some useful info.

---

### Post by lemonsCC on 2006-12-06
wouldn't starting a new session solve this problem...maybe I am not understanding.

Just have the default be gnome and you choose to use pekwm when you log in.

---

### Post by aysiu on 2006-12-06
If you install *xnest*, you should be able to do this: ```
sudo aptitude update
sudo aptitude install xnest
gdmflexiserver --xnest
```

---

