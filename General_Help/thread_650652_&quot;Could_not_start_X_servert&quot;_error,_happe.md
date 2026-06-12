---
title: "&quot;Could not start X servert&quot; error, happening randomly at boot!"
date: 2007-12-26
forum: General Help
---

### Post by sneax on 2007-12-26
Hello, when I start my computer I sometimes get this error:

[i]"Could not start the X server (your graphical environment)
due to some internal error. Please contact your system
administrator or check your syslog to diagnose. In the
meantime this display will be disabled. Please restart GDM
when the problem is corrected."[/i]

Since I am the system administrator, contacting him does not solve the problem. I don't know where the 'syslog' is so that doesn't help either. How can I fix this problem, or at least learn why it happens?

What I normally do is simply ctrl-alt-del which restart the computer and then most of the time it's gone. Only sometimes it happens. I have been getting this problem for a few weeks now, but never got round posting about it. Once it boots into the GUI all works perfectly.

Thanks in advance!

---

### Post by sneax on 2007-12-27
Small bump? Anyone?

I'm already happy with suggestion to another forum or whatever to solve my problem!

---

### Post by dcstar on 2007-12-27
> **sneax said:**
> Hello, when I start my computer I sometimes get this error:
..........
What I normally do is simply ctrl-alt-del which restart the computer and then most of the time it's gone. Only sometimes it happens. I have been getting this problem for a few weeks now, but never got round posting about it. Once it boots into the GUI all works perfectly.

Thanks in advance!

Intermittent problems like this can be very hard to pin down, they can be a combination of hardware initialisation and timing when various modules load at boot time.

You may want to investigate if your video hardware has some specific settings that you can put in your xorg.conf file so it doesn't rely on auto detecting some things.

I did this with my Nvidia hardware after having some issues, I had to put in a setting to set the output to the VGA port because it seemed to sometimes try to use the (non-existent) DVI output, and it seems to have helped.

---

### Post by sneax on 2007-12-27
Mmh, is there a way to check what the error output actually is? There must be some fatal error before the X server decides to shut down right?

I have an Intel Centrino laptop so it should be fairly well supported.

---

### Post by PmDematagoda on 2007-12-27
Post the result of:-
```
cat /var/log/Xorg.0.log
```

---

### Post by sneax on 2007-12-28
Thanks! I looked at the file and it will be of great help when it happens again! I'll put this thread in my favourites and when it happens again I'll come back - unless I can figure it out myself using that log.

Thanks for the clue!

---

