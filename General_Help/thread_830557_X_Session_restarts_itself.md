---
title: "X Session restarts itself???"
date: 2008-06-15
forum: General Help
---

### Post by windoze87 on 2008-06-15
I just installed Hardy Heron 8.04 (clean install). While doing miscellaneous things today, X decided to restart itself. Twice. To make sure that im conveying the correct thing (which i believe i am), it's like I log out of my current session, but I'm not doing it. My screen goes blank and then my GDM login screen pops up. What's going on here:confused:

---

### Post by sdennie on 2008-06-15
Are you using an nvidia graphics card?  If so, it's not completely uncommon for it to crash while doing seemingly innocent things (like dragging files in nautilus).

---

### Post by windoze87 on 2008-06-15
I am. I'm using the driver installed through EnvyNG. In /var/log/syslog, i see something that may point to whatever happened. the error message says ```
Jun 15 22:31:42 gdm [5510] gdm_slave_xioerror_handler Fatal X Error - Restarting :0(
```. Do i need to remove the EnvyNG version and downgrade? Also, i wasn't really doing anything... just reading an email, and then bam. Earlier when it first happened, i believe i had just sat back down in my chair lol

---

### Post by sdennie on 2008-06-16
Downgrading probably won't help.  I can crash X easily using the nvidia driver by plugging in a USB drive and trying to drag something to it in nautilus.  It's almost certainly an nvidia driver issue because upgrading to the latest drivers (173.14.05) causes a slightly less lethal behavior (it still makes the machine go crazy but doesn't crash X and, a Ctrl-Alt-F1 Ctrl-Alt-F7 brings it back).  

I can't offer solutions for your problem, just explanations: NVidia proprietary drivers are quite poor for desktop work (but good for games).

---

### Post by windoze87 on 2008-06-16
I wonder if this is an issue with 8.04... I used 7.04 for two months before finally downloading the new ISO and doing all that junk, and i never had a problem with X crashing on me in Feisty. I suppose I'll have to live with it since i like showing Compiz off to my friends, and i like the Emerald window decorator... i just wanted reassurance that my box wasn't going to explode lol so basically, im stuck with X bombing on me occasionally unless i uninstall my nvidia driver?

---

### Post by sdennie on 2008-06-16
It wouldn't surprise me if previous versions of Ubuntu didn't crash the X server.  Because NVidia is basically "out of the loop" when it comes to kernel and Xorg development, they are constantly playing catchup.  In the last year or so, the quality of the drivers has really suffered (especially for new hardware).

---

### Post by windoze87 on 2008-06-16
ah, well. It's not really a massive problem, i don't do much on Ubuntu that i'd freak out about losing when X crashes again. It only seems to happen after a few hours of being on the computer anyway, and I hardly ever spend more than two hours on it. Today's the first time i've been on for longer than that, cause i was excited about what new goodies and complications 8.04 has in store for me :) Thanks for the info & quick reply though. As long as none of my hardware's gonna fry because of this little driver problem, i'll be fine

---

### Post by sdennie on 2008-06-16
Your hardware should be fine.  One thing to note is that if you are using any special settings in /etc/X11/xorg.conf or using the new InitialPixmapPlacement/GlyphCache options, your machine is likely to be especially unstable.

---

### Post by windoze87 on 2008-06-16
the only thing i changed in /etc/X11/xorg.conf was some lines to get my monitor to accept a custom resolution (1440x1050, what Dell says is "optimum resolution" for my monitor). I'll put my xorg.conf.backup in place and see if going back to those settings will make anything better. And once again, thanks

---

### Post by durundal on 2008-06-16
Maybe you accidently hit shift and backspace at the same time, because that was restarting my session a lot while I was typing until I disabled it.

---

