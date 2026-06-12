---
title: "Program starts then closes after 1 second"
date: 2020-11-24
forum: General Help
---

### Post by alreve on 2020-11-24
Program starts then closes after 1 second

It happened before but with programs I didn't really need. I ignored it.
Sometimes also the desktop icons stop functionning, but lauching the program via the "Start/Application/Whatever" functions. 

Now it's Konqueror. I'm trying to set up a server so I really want Konqueror, it's both a browser and a file manager. I like drag-and-drop much better than typing ssh commands. 

It starts when launched from "Start/Application/Internet". I see the opened windows icons on the bottom (Kubuntu) moving aside to make room for a new icon. Then these icon move back in place and that's it. 

Lauching via the command line simply returns. No error message. Even if I type "konqueror --silent" (open without opening any default web page). 

I tried
apt remove konqueror
then 
apt install konqueror

I tried
[FONT=monospace][COLOR=#000000]sudo apt --reinstall install konqueror

I tried closing off a few opened windows (I tend to leave many windows simply downsized).

No changes. 

It used to run fine, the only thing that changed, AFAIK, was that I did an update/upgrade

Is there a way to force this program to run? 
Or at least a way to launch it via the command line in a kind of debbug mode, so that I would at least see an error message?

All suggestions welcome.[/COLOR]
[/FONT]

---

### Post by alreve on 2020-11-24
Functioning again, but only when launched via the command line. 
What did I do to fix it? Nothing more than previously stated.

I would still like to know an explanation and a fix, please.

---

### Post by jack-cowey on 2020-11-24
you might want to watch the journal when trying to open normally it might point to some app armour issue

```
journalctl -ef
```

---

### Post by CelticWarrior on 2020-11-24
This ^^^ and it can also point out other errors.
The point is nobody can troubleshoot such a problem without checking what's happening.

> [COLOR=#000000]Program starts then closes after 1 second[/COLOR]

[COLOR=#000000]It happened before but with programs I didn't really need. I ignored it.[/COLOR]
[COLOR=#000000]Sometimes also the desktop icons stop functionning, but lauching the program via the "Start/Application/Whatever" functions.[/COLOR]


So I suspect you have a pretty messed up system.
Uninstalling and reinstalling software to solve such things is a "Windows mentality" thing.

---

