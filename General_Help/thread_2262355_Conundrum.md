---
title: "Conundrum"
date: 2015-01-24
forum: General Help
---

### Post by Jedwinjim on 2015-01-24
Hi all, I've encountered a problem, and try as I might I can't seem to resolve it, here it is in a nutshell.

I've smashed the screen of my laptop.
I've used said laptop with HDMI connection to my TV for years with no issues. Rather than buy a new laptop (I'm skint right now) I thought I could just continue using my TV as the screen, no issues thus far. Yesterday however, unity seemed to just disappear from the screen, no dash menu, no menu bar at the top of the screen, just a desktop with a few desktop icons. I have no idea what has caused this, it's the same tv, same laptop, same HDMI lead, & I wasn't tinkering with anything, just watching movies, browsing the web, the usual.
Only desktop icons seem to work, ie. ctrl+alt+t does nothing. pressing the windows key doesn't bring up dash (it does nothing), pressing the power button does nothing! all I can do is access folders and the settings menu.

I thought, I know,I'll do a clean install,upgrading from 14.04 to 14.10 in the process, see if that eradicates the problem. Only when I come to the installation boot up screen the TV is the secondary input, not the primary (so of course I can't see the installation menus etc)

I found this workaround to switch the TV to being the primary screen [http://askubuntu.com/questions/344903/install-on-a-laptop-with-external-monitor-only](http://askubuntu.com/questions/344903/install-on-a-laptop-with-external-monitor-only) which works!!! Only problem is after I've booted and the TV is my primary display I need to edit the etc/default/grub so my laptop always boots with TV as primary display, but of course I cannot do this because ctrl+alt+t doesn't bring up my terminal (it does nothing!!) arrrrgh.... annoying.

My only other thought is the use of a VGA cable instead of an HDMI lead, can I expect a different result? or do they essentially do the same thing, will I still have the problem of not being able to make my TV the primary display? (I don't wanna buy a lead for nothing...)

Thanks for any help xxx

---

### Post by steeldriver on 2015-01-24
Can you get to a CLI "virtual terminal" (Ctrl-Alt-F1, Ctrl-Alt-F2 etc.) - that would be my first suggestion

---

### Post by Nutria on 2015-01-24
> **Jedwinjim said:**
> Rather than buy a new laptop (I'm skint right now)

Repair the laptop.  Replacement parts are usually available.

---

### Post by Jedwinjim on 2015-01-24
> **steeldriver said:**
> Can you get to a CLI "virtual terminal" (Ctrl-Alt-F1, Ctrl-Alt-F2 etc.) - that would be my first suggestion

yes I can! this is a brand new experience for me, are you able to give me a hand from here? or perhaps point me in the direction of a website/tutorial that would get me on the right track?

muchos gracias.

j

---

### Post by Jedwinjim on 2015-01-24
so with access to this virtual terminal & too much time on google I've found this guy experiencing the same error I got after reinstalling the unity desktop through console commands, he get's exactly the same error spit out at him that I did (compiz (core) - Error: Plugin 'opengl' not loaded.) , but I can't use his solution as when I run the 'ccsm' command I get "Error: 'nonetype' object has no attribute 'get_default_screen'

[http://www.reidmiller.name/content/some-annoyances-after-updating-ubuntu-1310](http://www.reidmiller.name/content/some-annoyances-after-updating-ubuntu-1310)

---

