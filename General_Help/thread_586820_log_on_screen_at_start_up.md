---
title: "log on screen at start up"
date: 2007-10-22
forum: General Help
---

### Post by quickshot89 on 2007-10-22
is there a way to disable the start up screen where you enter username password? it would be handy as i dont have a screen for this pc and i want to do things remotly

so, any ideas?

---

### Post by Ek0nomik on 2007-10-22
> **quickshot89 said:**
> is there a way to disable the start up screen where you enter username password? it would be handy as i dont have a screen for this pc and i want to do things remotly

so, any ideas?

The logon screen won't hinder your ability to do things remotely.  The logon screen acts as a security measure so people can't get into your box while you aren't around.  If you access your box via VNC or SSH, the logon won't prevent you from getting into your computer.  ( Assuming you get VNC setup on :0 )

That said, you can follow this to disable the logon for a specific user:

> Add the following line to the file /etc/shells

```
/bin/false
```

and change the shell for the mentioned user to /bin/false in the file /etc/passwd. It is the last entry in the line with the username in front.

---

### Post by quickshot89 on 2007-10-22
the thing is, i cant view the log on screen when im remotly viewing my linux box, it may be because im using vista thou, but cheers for the help, i will try the method out

edit: it wont let me change the file, says its read only

---

