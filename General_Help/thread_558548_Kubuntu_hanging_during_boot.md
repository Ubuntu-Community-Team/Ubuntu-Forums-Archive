---
title: "Kubuntu hanging during boot"
date: 2007-09-24
forum: General Help
---

### Post by lishevita on 2007-09-24
I've been running Feisty for a week on a new  Infinity laptop. Suddenly, this morning, it won't boot. I read through [this post]("http://ubuntuforums.org/showthread.php?t=490222&highlight=computer+doesn%27t+boot") and took a look at the tail of my Xorg.0.log. The last two lines there are:

Fatal server error:
Requested Entity already in use!

The lines before that are lines like:
             [nn] -1 0     0xhhhhhhhh - 0xhhhhhhhh (0x1) IX[B]

where n is a decimal digit and h is a hex digit. This means absolutely nuthin' to me. :confused:

Any ideas?

- Lisha

---

### Post by lishevita on 2007-09-24
I solved my own problem. 

I booted in recovery mode (as I had been since I realized that regular mode wasn't gonna boot no way no how), and then when it stops at the command prompt I took a look at my /etc/X11/ directory. I found that yesterday for some reason a new xorg.conf was written and there was an xorg.conf.1 in the directory, too. So, I'm guessing that some update I ran yesterday felt that my X server needed changing around. I moved the xorg.conf to xorg.conf.hold for just in case cases, and then moved xorg.conf.1 to xorg.conf. 

Voila! My um-puter boots. YAY! :)

Now, back to work...

---

