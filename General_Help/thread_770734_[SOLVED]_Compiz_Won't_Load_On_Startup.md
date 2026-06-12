---
title: "[SOLVED] Compiz Won't Load On Startup"
date: 2008-04-27
forum: General Help
---

### Post by alsamman on 2008-04-27
I have compiz working fine and everything and I have the tray icon installed. The tray icon I put as one of my sessions and that loads up but compiz won't load properly. When I right click on the icon and go to Select Window Manager, compiz is selected but not really working. Once I click on reload window manager it starts working but how come it doesn't work right on startup?

---

### Post by GCoffee on 2008-04-27
Are you talking about compiz or emerald theme manager?

If it is emerald, add this to your startup sessions

emerald --replace

Hope that helps

---

### Post by alsamman on 2008-04-27
> **GCoffee said:**
> Are you talking about compiz or emerald theme manager?

If it is emerald, add this to your startup sessions

emerald --replace

Hope that helps

no its compiz, awn does show and my screenlets look jagged and wobbly windows dont work, etc. until i reload the window manager

---

### Post by alsamman on 2008-04-28
bump

---

### Post by kgr132 on 2008-05-02
I'll second your bump. Same problem here. Right after startup, Compiz isn't working. It says it's the window manager but I have no desktop effects at all. I right click the Compiz fusion-icon and choose Reload Window Manager and then everything starts working as it should. I'm running a clean install of Hardy that used the RC1 CD image. My gutsy install had no such problems.

---

### Post by spinanicky on 2008-05-02
system => administration => session => add; 
name: fusion-icon 
command: fusion-icon 
This should put a small blue icon at the top right corner of your screen :P let me know if it works.. i was having the same problem up untill 4 hours ago and this fixed it :D

---

### Post by alsamman on 2008-05-02
> **spinanicky said:**
> system => administration => session => add; 
name: fusion-icon 
command: fusion-icon 
This should put a small blue icon at the top right corner of your screen :P let me know if it works.. i was having the same problem up untill 4 hours ago and this fixed it :D
i already have fusion icon as a session and it loads fine but compiz doesnt unless i right click on the fusion icon and click reload window manager.

---

### Post by halln on 2008-05-02
go to session name: compiz  Command: compiz --replace try that let me know

---

### Post by alsamman on 2008-05-02
> **halln said:**
> go to session name: compiz  Command: compiz --replace try that let me know

I tried that and it still did not work. It seems that when I boot, I see the AWN dock as everything is loading but then the desktop kind of refreshes and AWN disappears and none of the effects work, so I have to reload compiz so that it works. So it seems that Compiz is loading before everything fully boots, but then something is turning it off even though it says its still selected according to the tray icon

---

### Post by Superevil on 2008-05-02
I'm having the same exact issue since yesterday when I updated about a hundred packages over the web. I did the compiz icon at session startup after it didn't load. I never had to do that before. It won't let me apply the effects in the appearance dialog without loading the compiz icon first. Once the compiz icon is loaded i can quit it and everything works great until the next reboot. I'm having the issue in gutsy btw.

---

### Post by realstraw on 2008-06-02
I'm having the same problem on my thinkpad, have to reload window manager in order to have compiz working when start-up. However my desktop does not have this issue, everything loads correctly after every reboot. Anyone has a solution?

---

### Post by itsjustarumour on 2008-06-02
Same thing here, I had to reinstall Compiz from the standard Hardy repo because something else was broken, and now it won't load at startup.  Like the OP I can of course right-click the Compiz-Fusion icon and select "Reload Window Manager", but it would be nice if I didn't have to...

---

### Post by Reaved on 2008-07-05
I have removed compiz and reinstalled using synaptic and this problem remains for me.

[SOLVED]?

---

### Post by kgr132 on 2008-07-08
I still have a problem with Compiz not loading correctly at startup. I always have to reload it after I've booted up. Have already tried to reinstall it, etc. No change. After reading this thread, I don't see how the issue can be marked as "[SOLVED]". I saw no solution posted here.

---

### Post by hidinginthemountains on 2008-07-22
Just wanted to ditto this problem for me. Need to "Reload Window Manager" after login. Everything works just fine then.

[NOT SOLVED] 4 me

---

### Post by infiniah on 2008-07-24
I'm having the same problem as everyone else.

---

### Post by infiniah on 2008-07-24
Not solved

---

### Post by overdrank on 2008-07-24
alsamman is the orignal poster and has marked the issues solved. If you have the same issue then start a new thread or look at the FAQ's in my signature.

@ infiniah,hidinginthemountains, kgr132, Reaved

---

### Post by hidinginthemountains on 2008-07-25
Thanks for sayin :)

[New Thread]("http://ubuntuforums.org/showthread.php?p=5454330#post5454330")

---

