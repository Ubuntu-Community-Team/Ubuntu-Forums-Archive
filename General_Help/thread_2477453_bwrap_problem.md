---
title: "bwrap problem"
date: 2022-07-25
forum: General Help
---

### Post by vbgf3 on 2022-07-25
Hi Everyone,

I have this script which refuses to recognise the directory /otp/google/chrome, 

> setpriv  --inh-caps -all --ambient-caps -all bwrap \
--ro-bind /opt/google/chrome /opt/google/chrome     \
--ro-bind /lib/x86_64-linux-gnu /lib/x86_64-linux-gnu   \
--tmpfs /tmp \
--dev-bind /dev /dev \
--proc /proc \
--ro-bind /run/user/$(id -u) /run/user/$(id -u) \
--bind $HOME/Downloads $HOME/Downloads \
--bind $HOME/.config/google-chrome $HOME/.config/google-chrome \
--unshare-all \
--die-with-parent    \
--new-session \
/opt/google/chrome/chrome


It always responds with :  bwrap: execvp /opt/google/chrome/chrome: No such file or directory
However, if a place a --ro-bind /  /   at  the beginning of the file, then it works correctly. 
But I am thinking it is not secure to let the attacker roam freely around in a read only root. For one thing, the private home documents folder will be readable

---

### Post by The Cog on 2022-07-25
I suspect that /opt/google/chrome/chrome executable is trying to open something elsewhere, maybe in /var/lib, /var/run, /usr/lib, /etc - I really have no idea. All I can think of is to try giving it access to those at top level, and remove them one by one to see which ones it needs.

---

### Post by vbgf3 on 2022-07-25
So I added every folder immediately under root as --ro-bind . When I run the script, no errors are shown, but Chrome does not start. Buggy bwrap.

---

### Post by The Cog on 2022-07-26
I don't think you can blame bwrap. I think the problem is not understanding which resources the program needs. If adding every top directory as ro-bind, maybe it needs write access to something you haven't given it. 
Is it trying to create something in /var/run, for instance? Many applications create a lock file or socket in /var/run so they can tell if there is another copy already running.

You could try to get a better understanding of what chrome does by running **[FONT=Courier New]strace /opt/google/chrome/chrome[/FONT]** and looking for file opening calls. It's not a trivial task.

---

