---
title: "Unable to run Roller Coaster Tycoon using wine"
date: 2007-05-28
forum: General Help
---

### Post by Old *ix Geek on 2007-05-28
On one of my previous Linux laptops, I successfully installed and played Roller Coaster Tycoon using wine.  However, on my newest laptop (HP dv6000), although I was able to step through RCT's installation process, culminating with its registration screen, I'm unable to actually run it.  

For one thing, the installation didn't create a 'wine' entry on KMenu, as was the case in the past, so I wondered if it had actually completed successfully.

When I try running the program by navigating to it, an error modal comes up that says:

"Unable to initialize graphics system"

Any ideas what the problem might be...and how to fix it?!

---

### Post by MoLE on 2007-06-05
Which wine release are you using?  Which windows version are you configuring it under?

---

### Post by Old *ix Geek on 2007-06-14
Sorry I didn't notice the reply...I guess I'd given up on anyone responding!

In the meantime, I've done so much tweaking and fiddling around that I couldn't begin to tell you what I did that actually made it work.  And it does work--really nicely--with one exception: After 'saving' a game, the most horrific, annoying sound takes over and I can't make it stop without exiting and restarting the game.  I don't even know how describe this sound...the closest I can think of is static--LOTS of very loud static. :(

I'm using wine version 0.9.38, and I've tried win98 (wouldn't run at all--said there was no disc present), winxp and win2000...so far!

---

### Post by hikaricore on 2007-06-14
Are you using ALSA sound like suggested in the Wine Application Database?

[http://appdb.winehq.org/appview.php?iVersionId=400](http://appdb.winehq.org/appview.php?iVersionId=400)

---

### Post by Old *ix Geek on 2007-06-14
Yes, I was using ALSA sound, but I also had OSS checked [in winecfg].  I've shut that off now and after 3 or 4 attempts to make the DREADFUL sound recur...I couldn't!  I truly hope this solves that problem, because other than that it's playing really well.  (Right-click is a little flaky, but I've found a workaround so it's not a big deal.)

---

