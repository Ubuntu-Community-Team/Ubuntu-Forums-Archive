---
title: "Remove a log in session"
date: 2007-05-16
forum: General Help
---

### Post by Borg on 2007-05-16
Seems when I start it asks me which session I would like to log in to, how can I delete the unused session please ?

Thanks

---

### Post by hartz on 2007-05-16
> **Borg said:**
> Seems when I start it asks me which session I would like to log in to, how can I delete the unused session please ?

Thanks

[COLOR="Blue"]One way is to log into the "other" session, then just log out (don't switch).[/COLOR]

Another way is to use the following steps, eg if you don't have the password:

[COLOR="Green"]1. Open a terminal (Applications -> Accessories -> Terminal).  resize it so it is full-screen.

2. Identify the running sessions with this command
```
pstree -hp
```

3. Look for "gnome-session" of "xfce-session" or similar processes.

4. Once of these will be highlighted.  That is you current session, so that is not the "other" session.  Look at the process number in brackets after these other login-session processes.

5. You need to "kill" the other sessions.  run this command

```
sudo kill Processnumber
```

You will be prompted for your password.  Repeat until there are no more other processes.[/COLOR]

---

### Post by Borg on 2007-05-16
OK tried that, it only shows 1 session, what I mean is when I start the computer and put my user name in and password I then am given the choice of Default session or a second session. 

I think I might have explained it a bit vague :)

I don't need to pick between sessions as I'm the only user 

Thanks

---

