---
title: "Tty vs pty"
date: 2014-07-23
forum: General Help
---

### Post by orrymr on 2014-07-23
It all started off so innocuously. I was procrastinating beautifully on my linux machine and decided to play around a bit.
Casually I entered the $who command into my shell. My output was thusly:
```

orrymr   tty7         2014-07-23 10:12
orrymr   pts/1        2014-07-23 10:16 (:0.0)
orrymr   pts/2        2014-07-23 12:23 (:0.0)

```

tty7, I had read, refered to my X session, basically to the GUI which gets loaded and I use for most things, like browsing the web. It also turned out that by issuing ctrl + alt + F1-6 I could navigate to other login prompts.
I could get to other terminals. So, what was, then pts/1 and pts/2? Pseudoterminals, apparently. When I used xterm/konsole or the terminal app, it spawned a master and slave for some reason, and ptS refered to the slave end of it; the part that I interact with when I open up a terminal app. Or, more precisely when I open up a pseudo-terminal.

In my quest to understand the distinction between a terminal and a pseudoterminal I read that the difference was in the connection to the computer. This blew my mind. Once I had recovered the gray matter off the walls, I formulated the following question: why would these applications connect to the computer in different ways? And how?

To help clear this up I'd like to pose the following questions to anyone who will listen:
[LIST=1]
[*]Does the term terminal refer to any node connected to a server? 
[*]In modern computing, do we essentially have what used to be a server on our desks? Back in the day, would a terminal just be a keyboard and a screen? So, when you issued a command, it was sent to the server, the server did some processing, and sent back the result to your terminal? 
[*]Finally, what makes pty psuedo and tty not psuedo? Surely both would be psuedo, since we no longer connect to some remote server somewhere for our processing needs (well, mostly, if you don't think about cluster/cloud stuff). 
[/LIST]

As you can see, I've got some vague understanding of what's going on, but I'd really appreciate any help with this. Thanks :)

---

