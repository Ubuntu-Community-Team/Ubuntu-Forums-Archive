---
title: "Continuous swap and poor performances"
date: 2014-03-26
forum: General Help
---

### Post by matteo-dagord on 2014-03-26
Hello,
I've recently installed Xubuntu 13.10 64 bit on my pc ([COLOR=#101010][FONT=Ubuntu]Celeron g1610 dual core cpu, 4 gb ram e 500gb hard disk, with 5gb dedicatet to swap), but It's very slow. When I open an application (Chrome, Libreoffice, Gimp...) the system begins to slows down and to swap. I tried to decrease swappiness from 60 to 10 but nothing changes.
For example, yesterday I tried to open some photos with Gimp, but the system started swapping and the mouse pointer become jerky, so I wasn't able to work!
[/FONT][/COLOR][COLOR=#101010][FONT=Ubuntu]Previously I used Ubuntu 13.10 and it worked like a charm without particular settings. I use Xubuntu 13.10 with a older pc and it is ok, too.
What should I check?

[/FONT][/COLOR]

---

### Post by buzzingrobot on 2014-03-26
"swapon -s" and "free" in a terminal will display the current status of swap, including partition size and how much is in use.  It is also displayed in System Monitor's Resources tab.

---

### Post by ibjsb4 on 2014-03-26
With 4 gig of ram you shouldn't be using any swap.  Take a look at whats using memory in terminal.

```
top
```

and

```
free -m
```

What kind of video are you running?

```
sudo lshw -C video
```

---

