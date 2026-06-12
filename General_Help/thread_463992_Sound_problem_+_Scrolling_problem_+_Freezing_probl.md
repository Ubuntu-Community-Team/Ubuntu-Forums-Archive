---
title: "Sound problem + Scrolling problem + Freezing problem = Goodbye Ubuntu?"
date: 2007-06-04
forum: General Help
---

### Post by Jadd on 2007-06-04
Dear all,
This is my last attempt at fixing certain problems on Ubuntu before I uninstall it. The main two are:
[LIST]
[*]** no sound.** All suggestions I've found on the Internet just haven't worked, and all the posts which accurately describe my problem provide no answer. When I first installed Ubuntu Dapper on my PC, sound worked perfectly, allowing me to discover Amarok, the music app I love on Linux so far. However, after a week or two, the sound would suddenly stop working in the middle of a session, or even at boot-up. The only solution seemed to be rebooting and hope that this time, it would work. It did sometimes. When I killed then ran esd at the terminal,I got this error message: ```
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
```Finally, sound stopped working altogether, killing and running esd would give no error message but no sound either. So I decided to update to Edgy, but nothing changed.

[*]** freezing problem: ** every once in a while, for no apparent reason, the screen would just freeze up (or jam, as I like to call it). Hard disk usage would shoot up as indicated by the light on my box and its noise, and the ctrl-alt-F2 terminal was unavailable. It seems to be more likely to happen when I'm running the update-manager. This happened to me on Dapper and on Edgy. Again, my searches on the Internet only revealed people with the same problem as me, but without the solution.

[*]** slow scrolling: ** once I updated to Edgy, a new problem introduced itself: scrolling anything, whether in Firefox, Opera or Nautilus, was incredibly flickery and annoying. This flicker was so annoying that I switched back to Windows XP to write this post.
[/LIST]

These three problems are keeping me from using Ubuntu. If they don't become solved, I'm, at best, reinstalling Ubuntu Dapper, and at worst, abandoning Ubuntu altogether. Please help me before I post a 'I waved Ubuntu goodbye' thread in the testimonial section.:(

---

### Post by luptinpitman on 2007-06-04
You have a look at Feisty?  Possible that fixes were implemented in the newest release that were not available in Dapper/Edgy.

---

### Post by Jadd on 2007-06-05
They told me upgrading to Edgy would make things better, and it didn't. Why should I trust that Feisty will?
By the way, if I download Feisty as a CD ISO, can I use that to upgrade my Edgy installation? I may end up ugrading (again!) to Feisty, and if that doesn't work, reformating my ext3 partition and installing Feisty afresh on it.

---

### Post by Lucifiel on 2007-06-05
Could you post your the make of your sound card please? 

And by upgrading, do you mean upgrading via the repositories? 

I'm afraid to tell you this: when you perform a upgrade of any software, many of your existing problems will be "transferred over" as well.

You're far better doing a fresh install 'cos that'd likely give you a clean and mean machine.

---

### Post by Jadd on 2007-06-05
My soundcard, according to Belarc Advisor, is VIA AC'97 Audio Controller (WDM). But you can't blame my sound card, because it used to work on Ubuntu (and it works perfectly on Windows 98 and XP).
I upgraded to Edgy using gksu "update-manager -c"
A fresh install after just one month of using this OS doesn't give me a very good impression of it. I'd like to love Ubuntu, but I can't. It's not working.

---

### Post by arthur_kalm on 2007-06-05
Well if it's not working I assume your not using it :P. I'd try Fiesty out, at least the Live CD to see if the problems have been fixed (sound and scrolling). If it's working, then I suggest a fresh install. I've found that upgrading distros is not a good idea. If Fiesty works then there's nothing stopping you from using Fiesty for several years :D

---

### Post by Jadd on 2007-06-13
Well, thank you everybody for your help. I ended up burning Feisty Fawn live desktop CD, intending to upgrade my installation with that. Of course it didn't work, only the alternate CDs can upgrade! That should have been a bit clearer! So I reinstalled Ubuntu. Everything's working great now, I must have done something really stupid on my old installation.
Thank you everybody for your help! I hope all those other people who had sound problems get them fixed.

---

