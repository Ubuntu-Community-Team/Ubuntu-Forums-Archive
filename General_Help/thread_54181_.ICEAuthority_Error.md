---
title: ".ICEAuthority Error"
date: 2005-08-03
forum: General Help
---

### Post by artinla on 2005-08-03
When I log in, I get an error that says "Cannot read .ICEAuthority" and it shuts down gnome and returns me to the login screen.  This just all of the sudden happened without warning.  The only thing I may have done is a few updates in the past week. 

This has happened to me twice in the last few months.  It is a pain because I have to reinstall so many apps into the new user I have to create to get back in.

Anybody have an idea of what caused this?

What is .ICEAuthority?

Thanks,

Art

*Edit*  I found this thread that may explain it...  Other ideas are still welcome

[http://ubuntuforums.org/archive/index.php/t-1583.html](http://ubuntuforums.org/archive/index.php/t-1583.html)

Art

---

### Post by Takis on 2005-08-03
Try hitting CTRL+ALT+F1, logging in and typing ```
ls -l .ICEauthority
```
It should give you a result like this:
```
-rw-------  1 taki taki 195 2005-08-01 18:54 .ICEauthority
```
i.e. you're the owner and have read and write access to it.
If you're not the owner (this has happened to me before for some unknown reason) type
```
sudo chown artinla.artinla .ICEauthority
```
If you don't have read/write access (the permissions section should start '-rw' like mine did) then type
```
chmod +rw .ICEauthority
```
and then try logging in again graphically by hitting CTRL+ALT+F7 (after logging out from the terminal!)

---

### Post by Declan on 2005-08-03
I've had this problem twice, and the solution for me was SIMPLE.
I just deleted .ICEAuthority .
That's all.
You can do this in the failsafe terminal.
And then log in, and ICEAuthority (whatever it is, I haven't a clue) is regenerated automatically.  End of problem.
This worked for me.

Declan

---

