---
title: "No window titlebars in edgy"
date: 2006-11-03
forum: General Help
---

### Post by Dihi Doctor on 2006-11-03
I have just upgraded from dapper to edgy (using the officially recommended method, btw). All was fine until I rebooted to my new edgy desktop, where I found no windows have titlebars :S. There seem to be a few other GNOME problems, such as the desktop switcher widget and show desktop button not working.

I seem to remember having a similar problem when I used XGL/compiz (which is still on my system, although unused). Is it possible that the edgy installation has somehow "re-activated" this? How would I know?

But mainly, how do I get window titlebars to appear again? ](*,)

Thanks

EDIT:
Phew! Fixed it - it turned out that I had left gnome-window-decorator as a startup program (via System->Preferences->Session), which seemed to be broken :S. After disabling this and logging-out then in, all was fixed :)

---

