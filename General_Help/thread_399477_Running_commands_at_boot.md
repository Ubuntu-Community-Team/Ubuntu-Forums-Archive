---
title: "Running commands at boot"
date: 2007-04-02
forum: General Help
---

### Post by jamiethehutt on 2007-04-02
This seems a stupid question to be but does Ubuntu have a way of running commands at boot time? Something like Gentoo's /etc/inid.d/local and /etc/conf.d/local.start and local.stop. This is just to do things like run fusesmb and other little misc commands that don't really warrant and entire init script to themselves (or the user might not feel confident enough writing an entire script).

I've seen people suggesting putting commands in the auto started applications (on whatever desktop they run) but these don't run if your user never logs in, not something for use on multiuser systems.

If their isn't anything, I'll put together a init script to do it, write a tutorial and fill out whatever you guys do for bug reports/suggestions.

Also anyone know how to setup page up command completion like Gentoo does, thats where you press page up and it fills our your current command with ones you've typed previously?

I'm growing to quite like Ubuntu but I miss stuff like this from Gentoo...

EDIT: I've found the rc.local scripts, their not ideal though, still pretty ambiguous.

---

### Post by dcstar on 2007-04-03
> **jamiethehutt said:**
> 
........
Also anyone know how to setup page up command completion like Gentoo does, thats where you press page up and it fills our your current command with ones you've typed previously?
........

That sounds like a shell function, exactly what shell were you using in the other distro?

---

### Post by kerry_s on 2007-04-03
Yes, it uses /etc/rc.local

---

