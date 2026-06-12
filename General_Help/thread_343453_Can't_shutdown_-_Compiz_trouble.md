---
title: "Can't shutdown - Compiz trouble"
date: 2007-01-21
forum: General Help
---

### Post by kbsuperstar on 2007-01-21
I just installed Compiz! It took a ton of working around, but at least it's better than Beryl.

One big problem, though, is that when I try to shutdown (I click the "power button" in the top left corner) my computer just freezes. Well, I can move my mouse around, but I can't click anything else, and nothing pops up. I have to end up holding down my power button.

Hmm... any ideas? Thanks

---

### Post by pgilmon on 2007-01-21
Is it when you click the button that actually shuts down the computer or just the button that makes the shutdown-restart-hibernate menu appear?

In the second case, perhaps you will be able to shutdown by invoking the command

```
sudo halt
```

---

### Post by kbsuperstar on 2007-01-21
It freezes when I click the button that pops up the menu for "Shutdown, Restart, etc."

I'll see if sudo halt works :D

---

### Post by kbsuperstar on 2007-01-21
Yes, sudo halt works, but I would like to fix the menu for shutting down, etc.

Any ideas?

---

### Post by kbsuperstar on 2007-01-21
I realized that it doesn't actually make the computer freeze... well, it does, I think, but I can abort the "freeze" by pressing the escape key while my computer is "frozen." This just makes everything usable again... So, this is interesting.


Any suggestions on how to fix it, though, ha?

[edit]

Ok... so if I turn off GL Desktop, it let's me quit and stuff... Umm, yeah? Anyway to make it so I can shut down without having to deactivate GL desktop everytime?

---

### Post by insane_alien on 2007-01-21
sudo halt works? dammit, i've been doing 'sudo shutdown -hP now' for months.

---

### Post by kbsuperstar on 2007-01-21
Ha, k?

---

