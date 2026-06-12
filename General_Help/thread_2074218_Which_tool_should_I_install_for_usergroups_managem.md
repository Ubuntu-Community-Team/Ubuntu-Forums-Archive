---
title: "Which tool should I install for user/groups management?"
date: 2012-10-21
forum: General Help
---

### Post by Kivech on 2012-10-21
Hi all,

It's been a while that I have used Ubuntu seriously, but it looks that now I'll be using it for my work environment mostly.

I'm in QA of software development, and for this I need to work with VirtualBox a lot. That one needs access to my USB group though, but with the default 'user manager' that comes with 12.10, I cannot change the group permissions, and certainly not for applications.

Since Ubuntu is strictly not Gnome anymore, which app should I use to manage user and group permissions? But also for services, applications, and such.

Would the regular gnome tool work for that, or would that conflict with what Ubuntu comes with by default?

Thanks for any advice in advance.

Kivech

---

### Post by Cheesemill on 2012-10-21
Unity already uses the standard Gnome tool for user management, it just doesn't have the same functionality anymore since the advent of Gnome 3.

I just use the terminal for group management, for example to add a user to the VirtualBox group you can just do:
```
sudo gpasswd -a *username* vboxusers
```

---

### Post by Wim Sturkenboom on 2012-10-21
I started my own thread about this (just found this one too late), but an answer here will also do. I want a GUI tool for this, not a command line tool.

If the only way in the current Ubuntu desktop is a commandline tool, the user-friendliness has taken a serious knock.

---

### Post by wheeze on 2012-10-21
Install **gnome-system-tools** to get the good Users and Groups application back.

---

### Post by Cheesemill on 2012-10-21
> **wheeze said:**
> Install **gnome-system-tools** to get the good Users and Groups application back.
And then run ***users-admin*** to start it.

---

