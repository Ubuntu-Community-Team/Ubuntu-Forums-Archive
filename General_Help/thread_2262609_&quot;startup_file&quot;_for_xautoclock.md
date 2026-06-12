---
title: "&quot;startup file&quot; for xautoclock"
date: 2015-01-26
forum: General Help
---

### Post by robfindlay on 2015-01-26
Running Ubunutu 14.04 w/ i3 DE.

I need to find out something actually really basic. 

What is the best-practice for a dotfile to hold a set of startup commands. 

i.e. I need to load the following command at start up: "xautolock -time 1 -locker lock"

It actually works in my .zshrc file, however every time I start a new shell session I get an annoying message that it's already
running. Adding it to my .i3/config file doesn't seem to work at all. 

Someone on IRC suggested .login however zsh seems to ignore that completely. 

I know I could create a script or even alias the command but I was hoping for an automatic way to load it, thanks!

-Rob

---

### Post by oldos2er on 2015-01-26
i3 is a window manager, not a desktop environment.  :)

What line did you use in your ~/.i3/config file to try to launch the program? I'd try something like ```
exec --no-startup-id i3-msg 'exec xautolock -time 1 -locker lock'
```

---

### Post by robfindlay on 2015-01-26
> **oldos2er said:**
> i3 is a window manager, not a desktop environment.  :)

What line did you use in your ~/.i3/config file to try to launch the program? I'd try something like ```
exec --no-startup-id i3-msg 'exec xautolock -time 1 -locker lock'
```

I shall give that a try!

Now do you by chance know how to definitively disable 14.04 monitor sleep? I've tried everything I can think of.

-Rob

---

### Post by oldos2er on 2015-01-26
> **robfindlay said:**
> I shall give that a try!

Now do you by chance know how to definitively disable 14.04 monitor sleep? I've tried everything I can think of.

In default Ubuntu? No, I'm afraid I don't. I suggest you start a new thread for that question and I'm sure you'll get help.

---

