---
title: "[SOLVED] Gnome-pilot poping up at each Palm sync"
date: 2007-11-26
forum: General Help
---

### Post by NarsilAnduril on 2007-11-26
Hi,

Here's the problem :

I use J-Pilot to sync my Tungsten T3 and I'm very happy with it (works fine).

**But**

Every time I hit the sync button of the cradle, I have this f* gnome-pilot popup coming ...

How can I stop this ? I just don't need it and uninstalling looks difficult (ubuntu-desktop comes with it, strange dependency !) 

Could somebody help me ?

Thx

---

### Post by NarsilAnduril on 2007-11-27
Up !

That was working so fine with Edgy ... please help !

---

### Post by marcelo.matos on 2007-11-27
Fellow, i don't know if you solved your problem.

Anyway, on Gutsy, you could try this:

Go to
System->Preferences->Removable Drives and Media.

On the window, go to the PDAs.

Uncheck the "Sync Palm Devices when connected".

Or, on the list box below that, you can put the command of the software you want (jpilot, for instance).

I think that the default is: "gpilotd-control-applet". This must be the reason why it's opened when you try to sync.

Marcelo Matos

---

### Post by NarsilAnduril on 2007-11-28
That's it !

Thanks Marcelo, it was so easy ...

---

