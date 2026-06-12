---
title: "Linux newbie, screwed everything up."
date: 2008-05-21
forum: General Help
---

### Post by Twilight in Zero on 2008-05-21
Hi there. Thought I'd try out Ubuntu using Wubi. I know that Wubi's not so different from a normal install; I shouldn't need to post in the Wubi forum.

I installed 64-bit Ubuntu Hardy onto my Gateway MT6452, and I really liked it. Except... My wireless drivers kinda sucked. The whole RTL8187 thing (Or 8187b? I'm not sure) where it drops connection and doesn't even realize it. I can't do anything without a reliable internet connection, so I started to look for solutions.

This isn't about my wireless right now, though. After a prospective solution led me to ndiswrapper, I tried out several of my Windows wireless drivers. The last one I managed to try was the 64-bit driver. After I unloaded it, everything went to crap. I couldn't start any programs at all. I couldn't even bring up the quit dialog. Having no other way to get out, I just held my power button.

When I tried to go back to Ubuntu, I was greeted by a pleasant dialog that said that it couldn't start the GNOME settings daemon, and it had a close button that I couldn't click. I waited for a while, and just shut it off with my power button (the only thing it responds to; it shut down kind of normally). I tried again, and got the same thing.

I managed to brick it the same way once before, and just reinstalled the entire thing. But now I got most of my stuff set up the way I want it. Is there any other way to fix it?

I've been using computers for 19 years. That's my whole life. I know Windows very, very well. But I'm a total dummy with Linux. I don't know how to install drivers unless there's an installer, and much less remove bad drivers. I don't care about my wireless right now; I'll cross that bridge in one of the other forums once I come to it. I just want to fix **this** first.

Thanks in advance for any assistance. :)


EDIT: Somehow missed the beginners' forum. If this is more appropriate there, please feel free to move it there. :)

---

### Post by NIT006.5 on 2008-05-25
With regard to the gnome settings daemon error, check to see if your loopback address is working. If you can't ping 127.0.0.1 then that could be the problem, because the settings daemon seems to use that somewhere, or perhaps gnome uses that to connect to the settings daemon - not sure. This solved it for me though.

---

### Post by Cap'n Skyler on 2008-05-25
try the madwifi drivers.
there are a few different options that are included with Ubuntu.i use ndiswrapper and it is fine.you can also try an older windows driver(mine worked with 98,millenium and XP)
until:popcorn: you get it up and running can you just use the ethernet cable connection?

---

### Post by Cap'n Skyler on 2008-05-25
also can you get an Ubuntu ISO for your comp?
that might install and work better.sometimes when you have trouble that wont fix itself you can try to re install with another source.
 the ISO images for dvds and cds have some minor differences--IE if you had the same computer and tried from dvd.vd and the different versions,i bet all of them would install and be different with different issues to iron out.
welcome to the forums and good luck!!
post up again please

Moofs

---

