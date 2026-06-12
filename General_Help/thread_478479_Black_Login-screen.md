---
title: "Black Login-screen"
date: 2007-06-19
forum: General Help
---

### Post by Ambrevar on 2007-06-19
Hi there !

Now when I'm starting Ubuntu, I get a black loading-screen with the loading cursor, and nothing happens.
I think this is because i just tried to install a new login-screen theme.

How can I get it back ? Please help

Thanks in advance

---

### Post by Crafty Kisses on 2007-06-19
> **Ambrevar said:**
> Hi there !

Now when I'm starting Ubuntu, I get a black loading-screen with the loading cursor, and nothing happens.
I think this is because i just tried to install a new login-screen theme.

How can I get it back ? Please help

Thanks in advance

You should try reconfiguring your X server file:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Ambrevar on 2007-06-19
I'm not sure you have understood my problem : I just want to restore the default THEME (Human Theme) for the Login-screen (where the user name and password is asked on startup).
I don't think this has something to do with Xorg. I've tried it anyway, and it changed nothing.

I'm sure there is aconfiguration  file to specify login-screen theme, but I#ve no idea where it could be located.

---

