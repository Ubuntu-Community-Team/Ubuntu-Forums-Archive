---
title: "No &quot;User Management&quot; in System Settings"
date: 2012-12-22
forum: General Help
---

### Post by pwabrahams on 2012-12-22
I'm running Kubuntu 12.10.  I just discovered, when I went to add a user, that "User Management" is missing from the System Administration section of System Settings.  It used to come just before Date and Time.  What happened to it, and how can I get it back?

---

### Post by dniMretsaM on 2012-12-23
That's odd. I'm running Kubuntu 12.10 right now and User Management is right where it's supposed to be. Try typing "user management" into KRunner (Alt+F2) and see if it shows up.

---

### Post by pwabrahams on 2012-12-24
I didn't think there was a program named "user management", but just to be sure, I tried these things:
```
pa@morchella:~$ usermanagement
usermanagement: command not found
pa@morchella:~$ user management
No command 'user' found, did you mean:
 Command 'kuser' from package 'kuser' (universe)
 Command 'fuser' from package 'psmisc' (main)
 Command 'userv' from package 'userv' (universe)
 Command 'users' from package 'coreutils' (main)
user: command not found
pa@morchella:~$ usermanagement
usermanagement: command not found
pa@morchella:~$ user_management
user_management: command not found

```
I also tried the Alt-F2 method too, and the command again wasn't recognized.

I suspect there's some missing module, but I don't know what it is or how System Settings looks for it.

---

### Post by pwabrahams on 2012-12-24
I added the package **userconfig** and that solved the problem.  But it should have been there in the first place.

---

