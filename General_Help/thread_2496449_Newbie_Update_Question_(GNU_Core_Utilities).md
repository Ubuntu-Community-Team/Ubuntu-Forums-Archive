---
title: "Newbie Update Question (GNU Core Utilities)"
date: 2024-03-28
forum: General Help
---

### Post by karyk on 2024-03-28
I have my updates set to notify, and today I received my first notification that updates were available this morning.  Checking on details, the last one, GNU Core Utilities, was unchecked, and I could not check it.  I assumed that was because one of the other updates needed to be installed first.  That doesn't appear to be the issue though because running the update process again doesn't trigger an update.

Is there some reason GNU Core Utilities showed up but couldn't be checked?  Do I need to manually update it somehow?

---

### Post by Holger_Gehrke on 2024-03-28
It's a [phased update]("https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them"). You can tell by running 'apt-cache policy coreutils'. The output says 'phased 30%'.

Holger

---

### Post by karyk on 2024-03-28
Thanks, and thanks for the link, but I'm not sure that's it (although your answer and that policy makes sense).  I rebooted and that update (GNU Core Utilities)  and a few others then installed after I reran software updates.  So maybe that one (and the others?) needed something installed first?  It still shows 30% when I run that command.

---

### Post by Holger_Gehrke on 2024-03-28
As far as I know the percentage shown is the percentage of systems that will get the update at this time. Perhaps on the second attempt at upgrading the number of systems that had tried to update was so much greater that they chose a few more systems to get the update including your machine, although from what I've read the (random) contents of /etc/machine-id are somehow involved in the choice of what machines get updates in what phase of a phased update (see man 5 apt_preferences). The only thing I know for sure is that my system hasn't received coreutils 8.32-4.1ubuntu1.2 yet.

Holger

---

### Post by karyk on 2024-03-29
Perhaps my machine gets updates earlier than yours because it's a rather common HP device that is really crappy running Windows.  Lots of people have probably installed Ubuntu on them.  I didn't even keep a backup of the Windows setup since there's no way I'd ever want to run Windows on it again--way too slow.

---

