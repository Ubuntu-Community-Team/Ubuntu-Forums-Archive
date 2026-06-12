---
title: "Reattaching Tmux Session Automatically HowTo"
date: 2014-02-16
forum: General Help
---

### Post by NorthBridge4839 on 2014-02-16
I'm not sure if anyone else was having problems with this but if you use ```
chsh --shell /usr/bin/tmux YOUR_USERNAME
```
and try to use tmux as your default shell for logins, it will be pretty useless if you detach a session because when you login again, it will just spawn a new tmux session instead of reattaching to your first session. I found this to be pretty annoying and thought that it defeated the purpose of tmux detachment.

I just wanted to share a way to automate reattaching to your original session every time you log in. This only works if you detach (default is ctl+b and then d). If you exit (not detach) the session then it'll just spawn a new tmux session since there wouldn't be another (detached) tmux session to attach to.

Add this to your ~/.bashrc
```
if [ $"(tmux ls | grep 0: )" ]; then
        tmux switch -t 0
        tmux kill-session -a -t 0
fi

```

This is all assuming you set tmux to use bash by default by having this line in your /etc/tmux.conf
```
set-option -g default-shell /bin/bash
```

but that bashrc file will ask tmux to list any current sessions, specifically the first one which uses the "0:" designation. If the first session exists that implies that you detached from it and then it switches to it and kills all sessions but the one that you have just been reattached to. Otherwise if there is no detached session available, this statement does nothing and tmux goes about it's business and opens a new tmux session like it would normally.

Comment with any questions

---

### Post by Lars Noodén on 2014-02-16
Why not use something like this?

```

tmux a || tmux

```

That will try to reattach to the default session.  If no session exists, it creates one.

---

### Post by NorthBridge4839 on 2014-02-16
> **Lars Noodén said:**
> Why not use something like this?

```

tmux a || tmux

```

That will try to reattach to the default session.  If no session exists, it creates one.

That works and is what I used at first but every time you open a new bash shell in tmux, it'll give you a warning about nesting tmux sessions because I don't think you're supposed to use tmux attach while you're in tmux i.e. if it's your login shell. I don't think "tmux switch" cares if you're inside the session or not and won't give you any errors if you're switching into the session you're already in.

---

