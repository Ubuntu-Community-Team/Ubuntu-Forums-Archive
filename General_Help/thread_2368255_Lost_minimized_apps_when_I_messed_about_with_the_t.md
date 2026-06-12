---
title: "Lost minimized apps when I messed about with the taskbar settings."
date: 2017-08-08
forum: General Help
---

### Post by cheapodonuts on 2017-08-08
My fault I know, but we mess about, don't we?

 Anyhoo, I had to laugh at the time, because anything I minimized appeared to collapse immediately to the bottom of the screen,
 even though I had moved the taskbar to the top!!!! :lolflag:

And even after moving it to back the bottom, the result was the same and I still couldn't see what was minimized.

LUCKILY, I found a solution on askubuntu.com

Open a terminal and type
$ rm -r ~/.config/lxpanel
press enter

then type
$ lxpanelctl restart

press enter again and it's job done

No need to add sudo in front, this just worked! That's great since the info was posted in June 2015!

So I just thought I'd post this in case it helps anyone else.

[And there's the Askubuntu thread]("https://askubuntu.com/questions/64631/how-to-restore-the-default-lubuntu-panel?newreg=167c5adcaad34a95bc4311a02799759b") where I found it. :cool:

The poster mentioned that it may be overkill. But I'm not techy enough to know why.
 If this is bad practice or outdated info please let me know and I'll edit or a mod can delete it or whatever is necessary.

Have to buy myself a donut!

O:)  See ya!!!

---

