---
title: "Firefox: excessive memory usage"
date: 2007-04-17
forum: General Help
---

### Post by bjtuna on 2007-04-17
I am aware that Firefox has issues with memory leaks, and I've read plenty about the issues other people have had. However I am still rather concerned with the amount of memory Firefox consumes on my system after I've been using it for a few hours.    Right now, it's been running for just over 3 hours, and is consuming 225mb of RAM; this is after I had to restart it because it was using 400mb having been running since yesterday.

The details of my installation are below.  Is this something I could potentially solve through the removal of a bad extension, plugin, or combination thereof?  Or is this pretty common and I'm stuck with it?

This is Firefox 2.0.0.3 from the Ubuntu package on 6.10 on a Pentium 4 system with 1.5GB RAM.
No themes installed.

Extensions installed:
- Google Toolbar v3
- Web Developer  (setup to disable cache)
- Firebug
- FireFTP
- Gmail Notifier
- Tabbrowser Preferences
- DOM Inspector

Plugins installed (mostly via Automatix):
- Shockwave Flash v9
- Helix DNA Player
- Totem Webbrowser Plugin
- Windows Media Player Plug-in 10 (compatible; Totem)
- DivX Player
- QuickTime Plug-in 7.0 (compatible; Totem)
- Adobe Reader 7.0
- Java(TM) Plug-in 1.6.0-b105

---

### Post by xanikseo on 2007-04-17
One way of preventing excessive usage of RAM is to disable history caching, which allows the page to load fast when you go back. If you disable that feature, the RAM usage will go down. It will mean that when you go back, though, that the pages will load slower...

---

### Post by bjtuna on 2007-04-17
> **xanikseo said:**
> One way of preventing excessive usage of RAM is to disable history caching, which allows the page to load fast when you go back. If you disable that feature, the RAM usage will go down. It will mean that when you go back, though, that the pages will load slower...

I actually already did that; I set browser.sessionhistory.max_total_viewers=0 sometime last week but the problem persists.

---

### Post by Mike Buksas on 2007-04-18
I was hoping there would be more advice in this thread. Right now firefox is using 400 MB on my system.  This is bad enough to seriously degrade the performance of my, admittedly somewhat memory-light, machine.

Time to buy more memory, I think. I may try disabling the cache too.

Does anybody know which extensions are known memory leakers?

Mike

---

### Post by Telecaster72 on 2007-04-18
> **Mike Buksas said:**
> ...(snip)...admittedly somewhat memory-light, machine...(snip)...

1,5 gb is a dream for me who is running Duron1300/256mb ram:D :D 

Did you try Swiftfox? It behaves a little better on my machine esp. with the Fasterfox plugin.

I am also interested in what extensions are known for memory leaks though, so.....BUMP!

---

### Post by bjtuna on 2007-04-18
I found the problem, it's the extension called Firebug.  Disabled it, and memory usage stabilized.

Hope this helps!

---

### Post by Mike Buksas on 2007-04-18
> **Telecaster72 said:**
> 1,5 gb is a dream for me who is running Duron1300/256mb ram:D :D 

Did you try Swiftfox? It behaves a little better on my machine esp. with the Fasterfox plugin.

I am also interested in what extensions are known for memory leaks though, so.....BUMP!

I *wish* I was running 1.5GB. I've only got 512MB, so having 400MB taken by Firefox is hitting me pretty hard. Much thrashing of the hard drive ensues. 

I'll give swiftfox a try if I can't make an progress removing extensions. Thanks!

Mike

---

### Post by Mike Buksas on 2007-04-18
> **bjtuna said:**
> I found the problem, it's the extension called Firebug.  Disabled it, and memory usage stabilized.

Hope this helps!

Excellent. I wish that was my problem, but I'm not using that one. Did you let the Firebug developers know?

Mike

---

