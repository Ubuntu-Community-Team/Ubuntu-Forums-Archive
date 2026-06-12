---
title: "Freezes on shutdown? 8.04"
date: 2008-07-01
forum: General Help
---

### Post by Dansaycool on 2008-07-01
Ado, recently been having the problem with my 8.04 Desktop machine not shutting down correctly, you select shutdown from the menu and all the desktop icons and menus disappear but it then just hangs on the wallpaper, there's nothing else onscreen apart from the wallpaper and the mouse that you can still move about?

---

### Post by deadgobby on 2008-07-01
What is the make and model of your laptop or PC. Some systems do have this problem and could be a simple fix. 
Gobby

---

### Post by Dansaycool on 2008-07-01
Hey it's an ASUS T2-PH1 Barebone System, funny thing is it used to work fine shutting down, then all of a sudden it started freezing up. The only way you can get it to shut down is when it freezes press the power button on the case and then you see the screen change to the command line, looks the same as when you shut down the server edition. 
I'm not sure if it started playing up when I installed Apache2 and PHP and all them but I disabled them in 'Services' or so I thought

---

### Post by wrtpeeps on 2008-07-01
This has happened to me once or twice aswell.

---

### Post by Dansaycool on 2008-07-01
Was it only a temporary problem for you or a persistent problem that occurred on every shutdown?

---

### Post by shad0w_walker on 2008-07-01
If there is a solution to this issue I missed, I'm moving to 8.04. I had exactly this problem, which can be solved by hitting Ctrl-Alt-Backspace to kill Xserver, but it still bugs me to no end. That combined with scanning all my discs (700Gb+) at boot caused me to ditch 8.04, but turns out the disc scanning was a configuration problem caused by me and not 8.04 </getting off topic> 

I had a look around and most of the reports I saw were systems with Nvidia card (Nvidia in this as well) and my laptop which runs 8.04 doesn't have the problem (Has Intel intergrated graphics) so it might be a driver specific glitch?

---

### Post by Dansaycool on 2008-07-01
Yeah that disc scanning is a bugger, I got a 500GB hard drive and that takes time to scan through. I might try uninstalling all the software I installed as I didn't install that much. Still annoying though.

---

### Post by shad0w_walker on 2008-07-01
I traced my disc scanning down to a problem with fstab, turns out it was told to check my NTFS drive, which can't record when it was last checked, so it forced a check every boot to be sure.

---

### Post by shad0w_walker on 2008-07-10
Bumping up the week old thread.

Do any of you with this shutdown/logout problem have keytouch installed? I have found the solution for the issue (As fixed by someone else)

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg854070.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg854070.html)

Basically it's a ****up in the script that runs keytouch at login. I only needed to get the first couple of steps done to sort things out (I don't need to use the editor so I dodged that step)

---

### Post by Dansaycool on 2008-07-10
Ahh, bloody hell!! Yeah I had that installed for my multimedia keyboard! Grr I just reinstalled ubuntu to fix the problem lol
thanks anyway at least I know now what was causing the problem! 
Tar mate

---

### Post by shad0w_walker on 2008-07-10
No problem. Problem drove me up the wall and wanted to spread the love lol. Hopefully the package will get fixed soon enough and it can be permenantly put out of our minds, until then the fixes in the link work well enough.

---

