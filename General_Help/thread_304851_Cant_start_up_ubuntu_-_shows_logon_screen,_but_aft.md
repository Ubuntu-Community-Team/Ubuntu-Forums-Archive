---
title: "Cant start up ubuntu - shows logon screen, but after login it returns to logonscreen?"
date: 2006-11-22
forum: General Help
---

### Post by themota on 2006-11-22
Hi, I'm new to Ubuntu and linux. I'm running Ubuntu on my laptop, and have had this fail before. Ubuntu starts up as usual, but when I try to login at the login screen it go to a terminal-like environment for 2 secs, then return to login screen again. I get no failure messages or anything.
I am unable to login as you can hear, and the last time this happened a friend of mine helped me login... think he found the x-server id and used sudo kill... That's is at least what he says he did... How do I find the x-server ID?

I use the newest version of Ubuntu if that is any help... And gnome of course... Please help me, I have an really important assignment I have to deliver by mail within 4 hours, but can't access it...

---

### Post by Ramses de Norre on 2006-11-22
Could you check ~/.xsession-errors and /var/log/Xorg.0.log for errors? To do so: ctrl+alt+F1 to get a shell, you can get back to X with ctrl+alt+F7.

And to be honest: it may be the best if you just ask that friend how he fixed it last time because he'll probably know the answer and we may have to search quiet a bit via the forums to found it.

---

### Post by themota on 2006-11-22
> **Ramses de Norre said:**
> Could you check ~/.xsession-errors and /var/log/Xorg.0.log for errors? To do so: ctrl+alt+F1 to get a shell, you can get back to X with ctrl+alt+F7.

And to be honest: it may be the best if you just ask that friend how he fixed it last time because he'll probably know the answer and we may have to search quiet a bit via the forums to found it.

I will just try that... the problem is that my friends unavailable today, can't talk to him before tomorrow...

---

### Post by mdehoust on 2006-12-09
Any chance you can post the solution? I am experiencing the same thing running a 6.10 live CD on an old Gateway machine I inherited. Thanks in advance.

---

### Post by budgie9 on 2006-12-09
Seems to be fairly common happening. I had the same on one of my computers and was not able to resolve it even with help in the forums. A re-install got around it but that was not really needed I think.
So I will be interested int he solution.

---

### Post by SZF2001 on 2006-12-09
You could try the 6.06 version and get it to 6.10 online through the updater... But I dunno...

---

### Post by Kiwi Si on 2006-12-14
Hi,

I'm getting exactly the same problem - did anyone ever get a fix to this problem?

I too don't really want to have to reinstall the entire OS again.  :(

Thanks,


Simon

---

### Post by superhew on 2006-12-14
Yuck, I'm having the same problem... Has anyone filed a bug report? It seems to be a problem with the login manager, as it doesnt even start Gnome (or any other wm, for that matter). Anyone find any solutions? I can't bear another re-installation, they seem to happen too frequently...

---

