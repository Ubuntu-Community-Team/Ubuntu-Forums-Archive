---
title: "Failed to start X server"
date: 2007-01-09
forum: General Help
---

### Post by boyprodigy on 2007-01-09
Hi there

I was having screen resolution troubles and tried to fix it by "autoconfig"-ing xsever. I guess I screwed up because now when i try to start ubuntu up I get this

"Failed to start X server"

is there a way to fix this?

---

### Post by pissedoffdude on 2007-01-09
> **boyprodigy said:**
> Hi there

I was having screen resolution troubles and tried to fix it by "autoconfig"-ing xsever. I guess I screwed up because now when i try to start ubuntu up I get this

"Failed to start X server"

is there a way to fix this?

it should bring u to a command line, from there: ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by kevinf311 on 2007-01-09
When you are at the prompt (after x server fails) you should run a few commands.

First, back up your xorg.conf file 

```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
```

Then reconfigure your X server

```
 sudo dpkg-reconfigure xserver-xorg 
```

(I thinkl that is the right command, I'm not on my computer so I can't look at my cheat sheet :rolleyes: )

This should take you through a few prompts that should get your x session back in order. It's also a good idea to have a back up of a working xorg.conf file so that you can just move the back up over to the one that's not working instead of reconfiguring the whole thing. This is especially useful if you like poking around in xorg.conf and making customizations. Hope that this helps.

[Edit]Aw, pissedoffdude beat me to it!

---

### Post by boyprodigy on 2007-01-09
Great, it worked

and if fixed my resolution problem!

Thanks guys (or gals)

---

