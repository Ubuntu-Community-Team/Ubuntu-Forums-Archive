---
title: "Do you use tmux?"
date: 2020-09-22
forum: General Help
---

### Post by trpted on 2020-09-22
#1 I was browsing a website with a forum and found out that an user used something called tmux.

#2 I looked that up and found at least these:

[https://en.wikipedia.org/wiki/Tmux](https://en.wikipedia.org/wiki/Tmux)

[https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/](https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/)

#3 I am just wondering. Do you use Tmux?

---

### Post by TheFu on 2020-09-22
I don't, but power users with systems they need to reconnect to do.  Either **tmux** or **screen**. Which they use is probably more about which one their mentor used.  My connectivity is extremely stable, so I don't really worry about disconnections.

Lots of admins used to kick off long running tasks and watch them run in a terminal. I don't do that. Sending output to log files in /tmp/ by default is 2nd nature to me.

Lots of people can't live without tmux or screen. Most of their day is spent using those tools for terminal management.

---

### Post by scorp123 on 2020-09-22
> **trpted said:**
>  Do you use Tmux?

Absolutely. Can't do system administration without it.

---

### Post by scorp123 on 2020-09-22
> **TheFu said:**
>  Lots of people can't live without tmux or screen. Most of their day is spent using those tools for terminal management.

^ This.

---

### Post by dragonfly41 on 2020-09-22
I use [yakuake]("https://www.slant.co/versus/2449/11858/~yakuake_vs_tmux") for my workflow.

---

### Post by scorp123 on 2020-09-23
> **dragonfly41 said:**
> I use [yakuake]("https://www.slant.co/versus/2449/11858/~yakuake_vs_tmux") for my workflow.

It doesn't survive a disconnect, though. And disconnects can happen for millions of reasons, e.g. networker dude is messing with the network cables and the switches on your floor or down in the server room, or the guy responsible for WiFi is upgrading the firmware on the access points in the middle of the day (because he forgot to do it and fears for his life that his manager might find out ... so he does it right now during office hours), or you have to go into one of the few physical meetings and take your laptop with you ... aaaaand whoooops, WiFi is out of range all of a sudden and your SSH session dies.

Without **tmux** being able to survive these disconnects I'd be losing my work all the time.

---

### Post by dragonfly41 on 2020-09-23
I must admit that I don't suffer these experiences in my lockdown home bunker (other than tripping over cables)
but I can understand such  problems faced by pro systems administrators.
I am a solo developer and I use Yakuake in a development toolchain.

---

### Post by scorp123 on 2020-09-23
> **dragonfly41 said:**
> ... lockdown home bunker ...

OK, now I'm jealous :cool:

---

