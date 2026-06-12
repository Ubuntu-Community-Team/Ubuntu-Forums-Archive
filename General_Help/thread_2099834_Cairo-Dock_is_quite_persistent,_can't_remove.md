---
title: "Cairo-Dock is quite persistent, can't remove"
date: 2012-12-30
forum: General Help
---

### Post by 32EMCM on 2012-12-30
So I've been looking through all the other forum posts on this matter and quite frankly, after trying everything, nothing of help is at all mentioned. Here's my situation:

I'm using Ubuntu 12.10, and I find the launcher rather... plain, and misplaced. So I installed this app from the Ubuntu software center because I wanted something at the bottom, not to the left (I hate that you cant change that) and it was quite nice at first. It was pretty, it was functional, and above all else, could sit at the bottom of my screen. Well whoopdy-doo. Eventually, I was investigating ridiculous quantities of both persistent lag and lag spikes alike. After a while cairo dock crashed and that's when I saw it. The memory my computer was using dropped dead to less than roughly 3%, whereas it had been at 30-40% constantly beforehand. And so when the dock restarted itself, the lag returned, and so did the cpu usage. I didn't like that, and so I decided to hell with a fancy dock, it's just bloatware. That's when I discovered I cannot rid myself of it.

After trying various things; apt-get remove, apt-get --purge, kill-all, even tried all these with cairo-dock-plug-ins. I don't know what to do! Ubuntu software center declares its not installed, terminal cant find the packages for gods sake, and its still in my Dash Home! (Both Cairo-Dock (No OpenGL) and Cairo GLX Dock (OpenGL)) I've even gone through various dpkg syntaxes...

I've exhausted all my current Ubuntu knowledge and resources, so please help me figure this out. I haven't dealt with something like this since I deserted Windows 7 (and that was a while ago, I'll NEVER go back :3)

P.S. From what I've read this item is loaded in memory, whatever that means. Thought that may be of importance.

Thanks in advance,
-Will

---

### Post by ibjsb4 on 2012-12-30
Open a terminal and enter:

```
gksudo nautilus
```Then do a nautilus search on "cairo" and remove the leftovers.

Just be sure about what you remove, gksudo will let you remove anything and everything.

And maybe you can find a suitable dock here.

 [http://www.google.com/search?client=ubuntu&channel=fs&q=docks+for+linux+ubuntu&ie=utf-8&oe=utf-8#q=docks+for+linux+ubuntu&hl=en&client=ubuntu&tbo=d&channel=fs&ei=VNTgUMWsKeL2igK8tYGoAw&start=0&sa=N&bav=on.2,or.r_gc.r_pw.r_qf.&fp=fbe39fc67968a6ad&bpcl=40096503&biw=793&bih=743](http://www.google.com/search?client=ubuntu&channel=fs&q=docks+for+linux+ubuntu&ie=utf-8&oe=utf-8#q=docks+for+linux+ubuntu&hl=en&client=ubuntu&tbo=d&channel=fs&ei=VNTgUMWsKeL2igK8tYGoAw&start=0&sa=N&bav=on.2,or.r_gc.r_pw.r_qf.&fp=fbe39fc67968a6ad&bpcl=40096503&biw=793&bih=743)

EDIT:  Forgot one thing.  Make sure your in "FileSystem" in Nautilus when doing the search.

---

