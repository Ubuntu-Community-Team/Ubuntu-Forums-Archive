---
title: "Force user logout"
date: 2007-12-16
forum: General Help
---

### Post by Conspirator45 on 2007-12-16
Hey,
I am running ubuntu feisty and I would like to know how to force a user to logout, if possible. The  reason I want to do this  is because my brother keeps leaving his account logged but just switching user when he gets off. I have the root password. Thanks in advance.

---

### Post by r-mo on 2007-12-16
As the user:

[LIST]
[*]Run gconf-editor
[*]Navigate to /desktop/gnome/lockdown
[*]Tick the box for "disable_user_switching"
[/LIST]

You may want to disable_lock_screen too.

If you can't log in as the user I *think* you should be able to copy the configuration from:
/home/*user*/.gconf/desktop/gnome/lockdown/%gconf.xml
to the same location in their home directory.

---

### Post by Conspirator45 on 2007-12-16
Thanks for that. I will do that ASAP. But you didn't really answer my question. Is it possible to  force the user to log off?

---

### Post by r-mo on 2007-12-16
He'll lose any work (which is kinda why the lockdown thing is the better way) and it's very unclean but you can ctrl+alt+backspace to kill the session

---

### Post by Conspirator45 on 2007-12-16
So I cannot force his user to logout without the password?

---

### Post by jocko on 2007-12-16
ctrl+alt+backspace would kill all running x sessions, so yes, he would be logged out.

---

