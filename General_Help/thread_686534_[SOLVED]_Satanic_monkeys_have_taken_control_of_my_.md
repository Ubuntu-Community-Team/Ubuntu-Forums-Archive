---
title: "[SOLVED] Satanic monkeys have taken control of my Nautilus"
date: 2008-02-03
forum: General Help
---

### Post by itsjustarumour on 2008-02-03
I'm going nuts.

OK, I'll qualify that, I'm going even more nuts :lolflag:

Every time I reboot my Ubuntu 7.10 box, Nautilus fires up and opens my Home folder.  

I've not asked it to, and its not set up to start at boot in System>Administration>Sessions.  If I go to System Monitor>Processes and "End Proccess", within a couple of seconds it opens itself up again!

After several tries I finally managed to kill it off, and got this error message:

> Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem.

However, if I reboot my machine again, I'm back to square one  :confused:

I've been working on this machine all day,  I've not installed any software updates, the only thing I've done since this started happening about half an hour ago was some basic troubleshooting on some problems I'm having with gDesklets.  And I installed the Linspire CNR software this morning just because I was curious and wanted to see how it worked - I installed a couple of games to try it out, but I've done maybe 10 reboots since then with no problems until now.

Anybody got any ideas on whats causing this?

itsjustarumour

---

### Post by itsjustarumour on 2008-02-03
Well, I've tried killing bonobo-activation-server but no joy.

Totally mystified.....

Anybody?

---

### Post by S3Indiana on 2008-02-03
Any error messaging when you run Nautilus from the command prompt???

---

### Post by itsjustarumour on 2008-02-04
> **S3Indiana said:**
> Any error messaging when you run Nautilus from the command prompt???

Hi there S3Indiana,

Thanks for the reply.

No, no error messages when I run Nautilus in the terminal, seems to work fine.  But Nautilus is still firing up every time my Desktop loads...

---

### Post by zvacet on 2008-02-04
[This](http://ubuntuforums.org/showthread.php?t=199415&highlight=nautilus) is only thing i was able to find related to your problem.

---

### Post by itsjustarumour on 2008-02-11
> **zvacet said:**
> [This](http://ubuntuforums.org/showthread.php?t=199415&highlight=nautilus) is only thing i was able to find related to your problem.

Hi Zvacet,

Thanks for your post and for checking this out for me

Unfortunately, I don't have an "Automatically save changes to session" setting under System>Preferences>Sessions.  The only thing I have is "Remember currently running applications" under System>Preferences>Sessions>Session Options.  I've tried unchecking that, but still same problem!  :confused:

---

### Post by zvacet on 2008-02-11
Under System>Preferences>Sessions you have three tabs and last one is one you should click on and you will see described option.

---

### Post by pfx on 2008-02-12
I've been having this problem for over a month now, and it's making me want to stop booting into linux. I'd reboot, and my icons and desktop would be gone. Sometimes the user folder opens up and all the icons are messed up, along with the error message. Sometimes the error doesn't show up, but the same problem exists. The only fix I have is vigorously killing bonobo (... not the monkey) or restarting and sacrificing lambs to Zeus.

I used to be keen on figuring out how to solve linux problems, but after 2 years, I got really tired of it. I've never been more frustrated than when I connected a second monitor to use in windows with no intent to use in ubuntu a month ago, and the following tandem ubuntu threw at me. The only solution was to un-plug it. That's sort of when everything went ape-**** to be honest. Just giving a little background story.

The remember sessions thing has no effect for me.

---

### Post by rune0077 on 2008-02-12
Try it like this: open Sessions again. Click the last tab, "Session Options". Set your desktop to look exactly like you want it to look when you start up (meaning close everything you don't want to be there at startup, minus the Session window). Then hit "Remember currently running application".

---

### Post by itsjustarumour on 2008-02-13
> **rune0077 said:**
> Try it like this: open Sessions again. Click the last tab, "Session Options". Set your desktop to look exactly like you want it to look when you start up (meaning close everything you don't want to be there at startup, minus the Session window). Then hit "Remember currently running application".

Hi Rune,

That fixed it, thanks for that!

Cheers,

itsjustarumour

---

