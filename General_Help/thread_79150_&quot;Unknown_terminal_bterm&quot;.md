---
title: "&quot;Unknown terminal: bterm&quot;"
date: 2005-10-19
forum: General Help
---

### Post by Randy Sparks on 2005-10-19
I've booted from the 5.10 release CD and into rescue mode in order to reconfigure Xorg.

I issue the command "dpkg-reconfigure xserver-xorg" and am told:

```

"Unknown terminal: bterm
Check the TERM environment variable.
Also make sure that the terminal is defined in the terminfo database.
Alternatively, set the TERMCAP environment variable to the desired termcap entry.
debconf: whiptail output to the above errors, giving up!"
```

This also happens if I try and run the nano text editor. Vi works but moans about having to select a new terminal mode first. 

Any ideas?

---

### Post by Randy Sparks on 2005-10-20
Just tried the same thing using Hoary (5.04). The same thing happens. 

I don't know what the problem is but it seems to me that this could be a show-stopper of a bug - effectively it's rendering the rescue function of the disc useless. It means that you can't run any programs from the rescue command prompt. 

I think bterm might have something to do with foreign language support so perhaps I should point out that I'm setup for US English.

---

### Post by Randy Sparks on 2005-10-20
OK. Turning off the framebuffer at the boot prompt overcomes this problem:

ie typing

rescue debian-installer/framebuffer=false

Alternatively you can just type "rescue" as usual and define a different term environment at the prompt:

TERM=vt100; export TERM

Neither technique works perfectly and, to be honest, I'm on the periphery of my knowledge here (I don't fully understand terminal emulation). 

But at least this lets you enter some commands at the rescue prompt, above and beyond the lower-level file management commands. 

I would really appreciate it if somebody could tell me what the situation is here. Is this problem with bterm intentional and/or unavoidable? Or is it a bug?

---

### Post by Mustard on 2005-10-20
Couldn't you reconfigure xorg another way?  I've seen that many people doing it in IRC at #ubuntu, that I would have thought that there was no necessity for it to be done from rescue mode with the install CD.  What about recovery mode or even recovery mode and hit ctrl + c to get a login prompt?

---

### Post by Randy Sparks on 2005-10-20
Yeah, I realised that a little late. I completly forgot about the GRUB option for rescue mode. Reconfiguring Xorg from there works fine. 

Still, there are situations where you might need to use the install CD rescue mode - if GRUB isn't working, for example - and hopefully somebody might find the tips useful.

---

