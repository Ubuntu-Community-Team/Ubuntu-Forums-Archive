---
title: "Ubuntu freezes after login"
date: 2007-09-16
forum: General Help
---

### Post by azurelight1337 on 2007-09-16
Alright, so I've had Ubuntu working for at least 3 weeks, no problems.

That is until today. I tried to login, and it started loading my panels and desktop bg and everything, but froze after 2 seconds. I figured this was just a glitch or something, so I rebooted. Ubuntu ran fsck which ran fine, and then I attempted to login again. After 2 seconds, the screen flickered to the fsck screen, and back to the login menu. I attempted logging in again, and it froze again. I can login with root, but not with my account... 

Time to back-up and re-install Ubuntu, or is there a way to fix this? :confused:

---

### Post by JinxAu on 2007-09-16
Gday Azurelight,

It might be worth checking your permissions to your home directory. I have had dramas logging in when files can not be written to the home dir.

```
ls -l /home/$(whoami) 
```

Just in case, you might want to try resetting your home directory permissions using:
```
chown -R $(whoami):$(whoami) /home/$whoami
```

Hope that helps.

Cya round
Jinx

---

### Post by azurelight1337 on 2007-09-18
Uh... that's not what I mean...

Ubuntu logs in fine, but freezes when the desktop and panels are loading.

---

### Post by JinxAu on 2007-09-19
Sorry, thought you meant it was freezing when it is loading the services straight after login.

Got me stumped. :confused:

Cya round
Jinx

---

### Post by azurelight1337 on 2007-09-20
> **JinxAu said:**
> Sorry, thought you meant it was freezing when it is loading the services straight after login.

Got me stumped. :confused:

Cya round
Jinx

Unfourtunatly, it's not that simple.

For now, I've made a temporary user account, which works fine.

I think the issue is related to the desktop or panels...:confused:

---

### Post by azurelight1337 on 2007-09-22
bump

---

