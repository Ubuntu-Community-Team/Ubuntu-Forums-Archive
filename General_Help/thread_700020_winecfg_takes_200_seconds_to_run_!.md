---
title: "winecfg takes 200 seconds to run !"
date: 2008-02-17
forum: General Help
---

### Post by sayyeah on 2008-02-17
Hi all, after upgrading ubuntu for more than an hour, wine behaves in a strange way.
When I run any windows program, it takes very, very long time(usually >3 minutes) and launches finally.
For example, when I run:
> 
$ date; winecfg; date
Sun Feb 17 23:04:07 EST 2008
Sun Feb 17 23:07:29 EST 2008
(Of course, I immediately closed the winecfg window after it shows up to capture time.)

I also tested with pptviewer.exe, editplus.exe, ETC - they all need insanely long time to show up.
However, on the working panel, it says "Starting program" for a while and then disappears.
Can't find similar articles...since in my case somehow the program runs finally.

I "completely" removed from the synaptics manager and also deleted ~/.wine directory too.
After installing wine 0.9.54 and running winecfg again(it took >15mins to generate default files needed), it was the same.
In winecfg, I just selected "ALSA sound driver" and changed settings to "Windows XP".

On the system monitor, I found explorer.exe, wineboot.exe and wineserver running. (looks weird..)
Any idea ?!

Thanks in advance.

---

### Post by sayyeah on 2008-02-23
I don't know the reason, but it somehow solved after performing chkdsk.

---

