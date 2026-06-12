---
title: "Identify startup process source?"
date: 2014-10-07
forum: General Help
---

### Post by Grabbe on 2014-10-07
Hello!

I am having a bit of trouble with an autostarting xfce4-terminal that automatically uses the folder ~/scripts as working directory. Somehow this got enabled, but I can't find the source.

I've tried looking in all my config files, and the default ones, using grep, checking the GUI-startup manager etc. etc. Any ideas on how to debug this?

---

### Post by matt_symes on 2014-10-07
Hi

> **Grabbe said:**
> Hello!

I am having a bit of trouble with an autostarting xfce4-terminal that automatically uses the folder ~/scripts as working directory. Somehow this got enabled, but I can't find the source.

I've tried looking in all my config files, and the default ones, using grep, checking the GUI-startup manager etc. etc. Any ideas on how to debug this?

You're not 100% clear on what you are trying to achieve.

Do you want to stop the terminal automatically starting when you log in to the desktop ?

Kind regards

---

### Post by ajgreeny on 2014-10-07
Close any running applications then use the **Settings Manager->Sessions & Startup->Session** tab, click on the Clear saved sessions button, ignoring the warning, then click on the the Save Session button.

Also make sure that the **"Save session for future logins**" box on the logout dialog is not selected when you close down.  You should then always start with a new clean session other than any apps you have added to the startup list yourself.

---

### Post by Grabbe on 2014-10-07
> **matt_symes said:**
> Hi



You're not 100% clear on what you are trying to achieve.

Do you want to stop the terminal automatically starting when you log in to the desktop ?

Kind regards
Yeah, exactly.

> **ajgreeny said:**
> Close any running applications then use the **Settings Manager->Sessions & Startup->Session** tab, click on the Clear saved sessions button, ignoring the warning, then click on the the Save Session button.

Also make sure that the **"Save session for future logins**" box on the logout dialog is not selected when you close down. You should then always start with a new clean session other than any apps you have added to the startup list yourself.

This did it. Thanks! I'm more used to Arch than Ubuntu - sometimes the simple things are the hardest. :) I don't remember saving my session.

---

### Post by ajgreeny on 2014-10-07
Great!
Can you mark the thread as "SOLVED" from the "Thread tools" menu at the top please.

---

### Post by Grabbe on 2014-10-08
> **ajgreeny said:**
> Great!
Can you mark the thread as "SOLVED" from the "Thread tools" menu at the top please.
Done! :) Thanks btw. I'm new to this forum. I can't remove my own posts, is it supposed to be like that? I made an accidental post yesterday, too fast.

Ubuntu as a whole is a lot more pleasant than Arch in terms of maintenance - that's why I migrated after like two years. But is hard at the same this, because things sometimes happen automatically too often.

---

### Post by ajgreeny on 2014-10-09
All posts are meant to remain on the forum, even after being solved, as it gives a good chance that a search will find the info and other users might be helped out.

If you really post something totally out of context or by mistake you can click on the small "Report Post" icon at the bottom left and ask the moderators to remove it.

---

