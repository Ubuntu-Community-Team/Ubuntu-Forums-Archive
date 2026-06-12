---
title: "I installed a new ubuntu 24.04 (which may be a mistake)"
date: 2024-08-20
forum: General Help
---

### Post by jgw on 2024-08-20
I downloaded ubuntu 24.04 - I suspect its not quite ready yet but that may be me.  Anyway, one thing that's happening all the time is that the system is freezing.  This happens when I do something with the mouse (not the same thing).  It just happens.  I re-boot and its fine until next time.  The mouse just freezes and nothing will make the system unfreeze without booting.

I am also having problems with my system setup display.  On my other machines mine is set at 1920x1080 but with this one it says 1024x768.  My monitor is:
LCD Panel
Size23.6 " diagonal (59 cm)
Display area521.28 mm (H) x 293.22 mm (V)
Pixel Pitch0.2715 mm (H) x 0.2715 mm (V)

and considers 1920x1080 to be the one to have.  Before I installed this there wasn't a problem now, however, its 1024x768.  I have followed all sorts of things about making it 1920x1080 and failed at all of them.  

Thoughts?

---

### Post by werewulf75 on 2024-08-20
[SIZE=2]Given the delay and frantic efforts to get 24.04 out, I'm even more suspicious - call me paranoid! ;) - than usual that it's buggy as hell. Your mouse and monitor may have caught Noble out with its pants down perhaps?

If no solutions come forth here, I'd play safe and ditch the bugger and go back to 22.04 till at least the .1 or .2 release.
[/SIZE]

---

### Post by &amp;KyT$0P# on 2024-08-20
What graphics card do you have?
Are you using the same graphics driver in 22.04 and 24.04?

As a test, do the freezes happen if you boot with [FONT=monospace]nomodeset[/FONT] boot parameter?

When the system freezes, does it reboot in response to [Alt+SysRq, REISUB]("https://www.howtogeek.com/119127/use-the-magic-sysrq-key-on-linux-to-fix-frozen-x-servers-cleanly-reboot-and-run-other-low-level-commands/#cleanly-restarting-your-system")?

> **werewulf75 said:**
> Given the delay and frantic efforts to get 24.04 out, I'm even more suspicious - call me paranoid! ;) - than usual that it's buggy as hell. 

Same here.  Usually I try out the next LTS in a VM right away, but this time I'm waiting for 24.04.1 release before even doing that.

---

### Post by jgw on 2024-08-21
I thought to do exactly as you suggested.  So I googled "download ubuntu".  Sticking to ubuntu sources the first 4 were all for 24.04 and I gave up.  I guess I will just keep on chugging along with a mess.  Kinda off putting.................

---

### Post by yancek on 2024-08-21
The link below is to the ubuntu.com site to download 22.04 which was the first link show on a web search.  

[https://releases.ubuntu.com/jammy/](https://releases.ubuntu.com/jammy/)

---

### Post by jgw on 2024-08-24
I just realized that everytime I leave the machine for an hour or more that, when I get back, my system is now frozen as well.  Just can't wait for the next 24.04 has for me.

---

### Post by jgw on 2024-09-08
I kinda just gave up and it seems to fix this and that over time.  Very strange.  I will mark it solved.

---

### Post by werewulf75 on 2024-09-08
With the kind of history you've had here I wouldn't want to trust that system with anything. I'd go back to 22.04.4 - D/L link in a previous post.

---

