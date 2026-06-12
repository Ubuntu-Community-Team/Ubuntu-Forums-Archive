---
title: "How to log what happens each time process starts?"
date: 2012-11-02
forum: General Help
---

### Post by dobstera on 2012-11-02
Hi guys,

I have 4-core i7, 8G RAM, 2G nvidia video Asus laptop, running Ubuntu 12.10.
With these specs one would expect Ubuntu runs lightning fast, but thing is it's kind of sluggish. When I start a program (Chrome, Filezilla, Libre Office, Ubuntu Softwware Center, 720p video with VLC, etc.) for the first time after boot I get some 5-6 seconds of nothing. Then of course they kind of speed up when you close and reopen them several times. Even the dash seems slower than the demos I've seen on other setups.

I don't think this is OK, so I'm looking for a way to solve it. Is there a way to log the activity between the click of the mouse and the actual start of the program? If there is, maybe I can find something in common that is slowing down.

If you have other suggestions, they will be more than welcome ...

---

### Post by pbrane on 2012-11-02
Most of those apps are going to run on one core. They don't run in parallel on multiple cores. The first time you run them after a reboot all supporting libraries, are loaded first. It can take a few seconds. Subsequent runs usually are faster due to caching. Some apps like the software center need to read large files as well.

Not saying you don't have an issue but what you described seems normal to me. I don't know of a way to log what you want but there are ways to trace system calls, etc. I don't think that will help though.

---

