---
title: "&quot;s&quot; &quot;d&quot; and &quot;f&quot; don't type in console"
date: 2008-05-09
forum: General Help
---

### Post by krose on 2008-05-09
In zsh everything types just fine. However, in all other shells (bash, mysql, etc), and in the non-X console, the lower-case "s", "d" and "f" keys won't type. I only noticed this when trying to do some work in mysql (pretty tough without those three keys), and it must have worked at some point or I would have had a hard time switching to zsh (note the s). I switched to a dvorak layout (via the gnome keyboard app) and the "s", "d" and "f" keys still wouldn't type (though they were mapped to other physical keys).

I'm running gnome in Heron on a Dell D620 laptop.

Any ideas appreciated. I don't know where to start and I'm not getting very far googling for "s", "d" and "f" or "keys won't type".

---

### Post by krose on 2008-05-17
Some additional information...

First, these three letters always work fine in zsh, and always don't in bash and mysql. This is consistent in both X and at the system console. It's also consistent whether I change /etc/passwd and login in bash and then start a zsh session (via a script since I can't type an "s" while in bash), or login in zsh and then start a bash session.

Second, changing to a dvorak keyboard layout still had a problem with "s", "d" and "f", even though these letters were mapped to different physical keys.

Third, there's never a problem with captital "S", "D", or "F" -- only with the lower case letters.

Wierd, huh? I'm pretty sure it's due to some software keymapping that's incorrect but being corrected by zsh. However, I don't know where to start looking for this.

---

