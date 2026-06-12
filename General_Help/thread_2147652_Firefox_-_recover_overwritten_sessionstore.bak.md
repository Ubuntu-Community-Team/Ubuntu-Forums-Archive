---
title: "Firefox - recover overwritten sessionstore.bak"
date: 2013-05-22
forum: General Help
---

### Post by andreazzz on 2013-05-22
Hi all!

Several times now I have encountered the problem probably many of you already have experienced: someone (or something) closes your Firefox and doesn't use the "Recover Tabs"-function, which causes you to lose your opened pages. I already tried several programs as Testdisk and Photorec, but I can't get them to recover my .mozilla folder... Therefore I recovered my complete home folder, but after more than an hour (I cancelled) and it had already recovered over a tenthousand files in more than 100 folders. I searched them with the "find" command, but none of the files had the .bak or .js extension. Does anybody have a solution for this? Or is the only thing you can advice is to backup my "sessionstore.bak" in the future (for which I've written a script just today)?

Thanks for all your help!

Andrew

---

### Post by ohnonot on 2013-05-23
your probably more likely to find a solution on firefox/mozilla help pages then here.
anyhow, testdisk and photorec seem to be unsuitable for this. you could try searching temp or tmp folders, but my guess is, once firefox is closed forcefully, this info is lost. the solution would be to avoid forcefully closing ff.

---

### Post by andreazzz on 2013-05-24
I was already affraid there wouldn't be a solution. This will surely force me to install my backup script on all the pc's I use to prevent this in the future... (And I'm pretty sure it isn't possible to recover te tabs if I can't recover a overwritten file. And do temp folder contain those files? And if so: they would have been deleted if I have rebooted my pc?)

Thanks for your help!

---

### Post by ohnonot on 2013-05-25
look, i didn't say it's impossible; i'm not that much of a firefox or linux expert to give that kind of statement.
but i personally think that script you are using will probably be the best solution.
would you care to share it with the community?

ps: also sometimes it helps to tackle the problem from a different angle, like: why is ff being forcefully closed? could you improve sth there?

---

### Post by andreazzz on 2013-05-25
Well, I just wanted to hear someone else's opinion there I thought it was impossible, so thanks for that;)

Of course! The only problem is that I don't really know how to handle the fact that Firefox creates random profile names, maybe do you know it?

Well, the problem is other people closing my Firefox and then restarting FF(: I don't think I'm able to handle that :p

---

### Post by ohnonot on 2013-05-25
> **andreazzz said:**
> Well, I just wanted to hear someone else's opinion there I thought it was impossible, so thanks for that;)
Of course! The only problem is that I don't really know how to handle the fact that Firefox creates random profile names, maybe do you know it?
Well, the problem is other people closing my Firefox and then restarting FF(: I don't think I'm able to handle that :pi've been wondering myself, why the random profile names... maybe it's some kind of security thing.
unfortunately i have no experience at all with multi-user machines. good luck!

---

