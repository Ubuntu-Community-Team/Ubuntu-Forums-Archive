---
title: "Possible to have programs start when gnome starts on a specific VT?"
date: 2004-11-17
forum: General Help
---

### Post by HiddenWolf on 2004-11-17
I've added some programs, like mplayer and gaim, to come up automaticly on boot.
However, I prefer gaim to come up and put the buddy-list on VT4, rather than cluttering my workspace.

Is there any way to do this?

---

### Post by jdong on 2004-11-17
ooh, this seems like a harder one to answer. Perhaps ask on gnome's mailing lists. A google didn't turn up any helpful hits.


*Moving to Stumper Questions

---

### Post by ctbarrett on 2004-11-28
I believe you're looking for something like [this](http://www.burtonini.com/blog/computers/devilspie) -- "Devil's Pie:  A window-matching utility, inspired by Sawfish's "Matched Windows" option and the lack of the functionality in Metacity ... Devil's Pie can be configured to detect windows as they are created, and match the window to a set of rules. If the window matches the rules, it can perform a series of actions on that window. For example, I can make all windows created by X-Chat appear on all workspaces, and the main Gkrellm1 window does not appear in the pager or task list."

---

### Post by tomchuk on 2004-12-11
I believe you're talking about Virtual Desktops, not Virtual Terminals. VT4 is accessed by  pressing Ctrl + Alt + F4. You can run a seperate X session on VT4 and choose to launch gaim there, but I think what you're talking about is virtual desktops.

The app you're after is [wmctrl](http://sweb.cz/tripie/utils/wmctrl/) which provides a command line interface to the Extended Window Manager Hints spec.

Something like this:
```

/usr/bin/gaim &
/usr/local/bin/wmctrl -r "Buddy List" -t3

```
will launch gaim and move it to virtual desktop 4 (counting from 0).

On my box the "Buddy List" isn't matching the window title properly, so I use some grep/awk madness to grab the window ID and use that with the -i switch:
```

/usr/bin/gaim &
wmctrl -i -r `wmctrl -l | grep '[Buddy List]$' | awk '{print $1}'` -t3

```

---

### Post by jdong on 2004-12-11
excellent, you guys!

---

### Post by Caboto on 2005-07-16
Sorry for bumping up old threads. But my question refers to exactly this problem and another search through the forums didn't help me out...
[QUOTE=tomchuk][...]
On my box the "Buddy List" isn't matching the window title properly, so I use some grep/awk madness to grab the window ID and use that with the -i switch:
```

/usr/bin/gaim &
wmctrl -i -r `wmctrl -l | grep '[Buddy List]$' | awk '{print $1}'` -t3

```[/QUOTE]
Great. That did work for me (except that i only needed 'Buddy List'). But now comes the tricky part. I would like to move my ThunderBird to Workspace 5 (i.e. -t4) right after startup. But even if i put Thunderbird before all others programs from the session (chosen 45) and give the wmctrl command the last id (so 200) it does not work. Seems like Thunderbird starts too slow...
Got anyone a idea? Could a a bash script help, which is started with by id 200, but need to wait for at least 2 seconds or so? If yes, could someone help me out with that? I'm not familiar with writing bash scripts.



Edit: Sorry, didn't noticed I'm in the warty board. I use hoary... But don't think it will make a difference.

---

