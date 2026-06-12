---
title: "After unlocking screen, Authenticate window will not go away"
date: 2015-05-01
forum: General Help
---

### Post by stretch4 on 2015-05-01
Whenever I unlock my computer, this Authenticate window pops up, saying "Authentication is required to change your own user data."

It doesn't matter how many times I click Cancel or enter my password and click Authenticate, it won't go away.

I'll attach a pic of the window.

---

### Post by kerry_s on 2015-05-01
in terminal:
rm -rf ~/.local/share/keyrings

that will delete & reset, next time your asked to set the password leave it blank, just press continue.

you can also do it from settings, but from term is easier.

---

### Post by stretch4 on 2015-05-02
> **kerry_s said:**
> in terminal:
rm -rf ~/.local/share/keyrings

that will delete & reset, next time your asked to set the password leave it blank, just press continue.

you can also do it from settings, but from term is easier.

That didn't make any difference.

---

### Post by kerry_s on 2015-05-02
> **stretch4 said:**
> That didn't make any difference.

alright, what app is it ? sounds like something that is running as root.

---

### Post by stretch4 on 2015-05-02
Nevermind. It worked after I rebooted.

---

