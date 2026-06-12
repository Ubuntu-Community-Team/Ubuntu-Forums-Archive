---
title: "Strace output for my Firefox crashes"
date: 2007-12-19
forum: General Help
---

### Post by Chriswaterguy on 2007-12-19
My Firefox crashes (freezes) frequently - one of the constant stream of bugs and instabilities that I've found with Ubuntu :(. I usually run Firefox with a lot of tabs open (10, 20 or more) but I've also had it crash with only 6 or 8 tabs open.

I met a system architect who was amazed at the problems I've had (he also runs Ubuntu on a Thinkpad and says he has had no problems). He gave me the very useful tip of running Firefox from a terminal using the command: 

> strace firefox

So when it crashed I copied the output from strace. I did this 3 times. The first two times I had to end the process; the third time I immediately left the computer when Firefox froze, and it was able to shut down by itself. 
1: [http://pastebin.com/f4bb5d16e](http://pastebin.com/f4bb5d16e)
2: [http://pastebin.com/f514d1357](http://pastebin.com/f514d1357)
3: [http://pastebin.com/f75d5a4e5](http://pastebin.com/f75d5a4e5)

Can anyone interpret this? Any input very welcome! 

A bit more context - I'm using a Lenovo Thinkpad R60. The system architect I met wondered if I had hardware faults. 

He also looked up something about BIOS and said there was a problem with the original BIOS on my machine, that could cause problems on waking up from hibernation, so he found a BIOS upgrade file (ISO, which I burnt to CD; I then ran the upgrade - I made the judgement that I could trust him). It didn't change things though. 

Thanks!

---

