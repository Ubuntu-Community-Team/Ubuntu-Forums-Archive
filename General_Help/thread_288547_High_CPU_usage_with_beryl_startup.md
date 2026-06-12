---
title: "High CPU usage with beryl startup"
date: 2006-10-30
forum: General Help
---

### Post by andnobodyslept on 2006-10-30
I keep having an annoying bug happen whenever I boot with beryl as my windows manager. As soon as I log in I have about 100% CPU usage. This just started happening when I upgraded to Edgy. I've noticed some people complaining of similar problems but no one with any answers. At least as far as I can find. I can startup fine in Metacity, and then switch over to Beryl, this is no problem. It's just when I startup with beryl, and it doesn't happen every time, just more times than not. Also a lot of problems with beryl and opening pdfs in firefox...but that is for another day.

Specs,
Intel i810 integrated graphics,
3Ghz P4
1 gig ram

Thanks

---

### Post by andnobodyslept on 2006-11-02
I hate to do this, and I'm only doing it once. Bump.

---

### Post by odelay on 2006-11-05
Wish I could help.  Right now the best I can do is say I'm having the same problem.

*I had "beryl-manager" set as a login item...this caused my CPU to go to 100% when starting in either Gnome or XGL.
*Disabling "beryl-manager" as a startup allowed me to work fine in Gnome and fixed the CPU problem in XGL, however it also kept beryl from working of course
*I'm using ATI drivers that show proper Direct Rendering in Gnome but gives back an X-Free-86 error from fglrxinfo in XGL

Do you know how to manually start beryl in XGL?  When I type "beryl" the manager pops up and all the windows go crazy and I pretty much have to restart (if I can).  Hopefully *someone* will figure this out. :(

---

### Post by andnobodyslept on 2006-11-05
Basically what I do is that everytime before I shutdown or reboot I switch over to metacity, that way when I bootup I it starts up in metacity, with the beryl manager, and I just start up beryl from there without any problems. But I'm useing intel integrated i810 with AIGLX. Hope that helped.
Good Luck

---

### Post by odelay on 2006-11-05
Glad that works.  I also found a [solution]("http://forum.beryl-project.org/topic-5682-titlebar-blinks") that works great for me (and is perhaps a little more convenient than manually changing the prefs every time).

In summary you want to make a script that stops then starts emerald and run it as a startup item--copied from my post in another thread.

Make the script

```
sudo gedit /usr/local/bin/start-xgl.sh
```
Add this to the script
```
cat /usr/local/bin/start-xgl
#!/bin/sh
beryl-manager &
killall emerald
emerald &
```
Go to Prefs>Sessions>StartUp and add "sh /usr/local/bin/start-xgl.sh"

There's probably a better way to do the script thing (maybe making it an exec) but this worked for me at least.

This has worked for several people, so I think it's worth trying and will make everything a little less "messy".

---

### Post by andnobodyslept on 2006-11-05
Thanks for the tip, but I don't think this will work for me, mainly since I'm not useing XGL, I'm useing AIGLX. Glad you got this figured out for you, but I will keep on looking.
Thanks again,
Ian

---

