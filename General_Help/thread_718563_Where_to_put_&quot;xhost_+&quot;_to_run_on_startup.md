---
title: "Where to put &quot;xhost +&quot; to run on startup?"
date: 2008-03-08
forum: General Help
---

### Post by Tuna-Fish on 2008-03-08
I need to have apps from several users visible on the same desktop at the same time. I can do this by running "sudo xhost +(name)". Where can I put this so it runs every boo up, so I don't have to do it manually?

/etc/init.d/rc.local would sound like the logical choice, but it doesn't work. Apparently I need to do it later on the boot or something.

Any help?

---

### Post by chrisccoulson on 2008-03-08
AFAIK you need to run xhost on the X display that you're trying to control access to, so I wouldn't expect it to work from rc.local.

And I don't think you need to run xhost with sudo either.

---

### Post by dcstar on 2008-03-08
> **Tuna-Fish said:**
> I need to have apps from several users visible on the same desktop at the same time. I can do this by running "sudo xhost +(name)". Where can I put this so it runs every boo up, so I don't have to do it manually?

/etc/init.d/rc.local would sound like the logical choice, but it doesn't work. Apparently I need to do it later on the boot or something.

Any help?

System-Preferences-Sessions-Startup Programs

I do it so my Boinc Manager displays work.

---

