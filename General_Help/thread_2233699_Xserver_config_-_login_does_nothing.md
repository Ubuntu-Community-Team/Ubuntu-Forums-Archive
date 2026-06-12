---
title: "Xserver config - login does nothing"
date: 2014-07-10
forum: General Help
---

### Post by wolfgangus on 2014-07-10
Hello,
        So I recently decided to try out KDE 4.13 on my xubuntu desktop. I did not like it, so I removed kde from my packages using apt. I also deleted a .kde folder in my /home directory.  The problem I am facing right now is when I try to login to my xfce or xubuntu session, the screen turns black and then returns me to the login manager again. I tried alt +f2 to get into CLI mode and startx, but it gives me some error on failure to authorize /home/username and some other crap. What log files would you guys like me to post?

My xinitrc does "exec startxfce4" if anyone is curious.


Thanks.

---

### Post by Bashing-om on 2014-07-10
wolfgangus; Hi !

That condition makes me question the authorizations on the .Xauthority and .ICEauthority files in your /home directory. They should be owned and grouped to "you".
```

ls -la ~/.Xauthority
ls -la ~/.ICEauthority

```
//
This is what is now suggested for the 'exec' line in ~/.xinitrc file:
```

exec startxfce4 --with-ck-launch

``` ( I also like many here, run xfce4 for my chosen DE)

Else: perhaps consider reverting xfwm to the defaults ?

[INDENT][INDENT]it's ubuntu
[INDENT][INDENT][INDENT][INDENT]fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

