---
title: "iBus shortcut preferences are not honored"
date: 2013-06-14
forum: General Help
---

### Post by NickLanam on 2013-06-14
Hello,

Before I file a bug report about this, I want to be certain that it isn't a configuration fault on my end.

I recently started using iBus to type Hangul (&#54620;&#44544;). This works perfectly. However, the default enable/disable shortcut (Ctrl+Space) is not optimal, as it conflicts with Eclipse. So, I decided to change this shortcut to Ctrl+Meta+Space in the iBus preference dialog (click the system tray icon, click preferences, edit the shortcuts field so that the only one is Ctrl+Meta+Space, click close, as there is no apply). The old shortcut still worked, and my new one didn't. I restarted iBus, the application that I was typing in, and the whole computer to be safe. Still, the old shortcut works and the new one doesn't, even though my changes ARE reflected in the preferences dialog of iBus where I changed them originally.

Where should I look for the problem here (and is there a workaround)? My first suspicion is that it's a bug, but I'm not ruling out my own fault.
[On a possibly related token, all of the Grid plugin's Ctrl+Alt+Something shortcuts all try to trigger as soon as I press Ctrl+Alt, so I had to disable all of them - this might indicate that the problem lies a bit deeper]

Ubuntu 13.04, Kernel 3.8.0, every installed package is pretty much standard.
One thing of note: I own the Ideazon MERC ([images here]("https://www.google.com/search?site=&tbm=isch&source=hp&biw=1504&bih=915&q=Ideazon+MERC&btnG=Search+by+image&oq=John+Kerry&gs_l=img.3..0l10.1459.3105.0.3362.10.9.0.1.1.0.135.720.6j3.9.0...0.0...1ac.1.9.img.Rwr16evOnaE")), and I've been mapping it with xev+xmodmap for several years under various flavors of Linux.

Thanks!
Nick

EDIT: My error. I confused Meta with Super.

---

