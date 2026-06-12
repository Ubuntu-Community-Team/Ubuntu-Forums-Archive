---
title: "dbus-daemon-1 doesn't exit"
date: 2004-11-05
forum: General Help
---

### Post by jayavarman on 2004-11-05
Hello,

I don't like to use gnome, so i use ion and i like to setup my X session in ~/.xsession . So i installed ubuntu and tweaked all these things. I start GDM with the option Session=custom which I think is the right one with this setup. Now, X in ubuntu is configured to always start dbus with the option --exit-with-session, so far so good. The problem is that this is _not_ what happen. When i kill my X session either with ctrl+alt+backspace or by exiting the WM, the following process:
```
dbus-daemon-1 --fork --print-pid 8 --print-address 6 --session
```
does not end and if I log in again a new identical one is created...

I know how to deactivate dbus but this is a strange behaviour anyway. Anybody has this problem? is it a bug and thus should be reported in bugzilla?

thanks

---

