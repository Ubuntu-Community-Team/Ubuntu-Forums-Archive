---
title: "Amarok/ALSA Troubles. Help Me Out"
date: 2005-10-25
forum: General Help
---

### Post by PhogHawk on 2005-10-25
Hey everyone, my system seems to have an oddity in the fact that Amarok freezes my entire system within a few minutes of playback; often on a track change. 

Everyone raves about Amarok, and what little time I have been able to spend with it has been wonderful. This problem has been recurring through two Ubuntu Versions (5.04 and 5.10) and two soundcards (Built-in motherboard kind and Soundblaster Audigy).

Amarok output flaws seem to be mostly related to DCOP errors if that helps. I'm also thinking it could be an ALSA problem because my system freezes on some other audio playback in Rhythmbox and such. Although errors are more abundant in amaroK.

If anyone can help me out or is experiencing the same problem, help me out. You can reply hear or AIM me at: PhogHawker. Email is also an option at: phoghawk (at) phoghawk .com.

---

### Post by mlomker on 2005-10-25
The dcop errors seem to be permissions related.  Try running it from a command prompt as **sudo amarok** and see if it behaves any better.

You could considering compiling your own using [my how-to.]("http://www.ubuntuforums.org/showthread.php?t=80492")

---

### Post by hoe on 2005-10-25
I use Amarok all the time. I did have similar problems when using the Arts Engine but l use the Xine Engine now and no problems.

Wayne

---

### Post by PhogHawk on 2005-10-26
[QUOTE=mlomker]The dcop errors seem to be permissions related.  Try running it from a command prompt as **sudo amarok** and see if it behaves any better.

You could considering compiling your own using [my how-to.]("http://www.ubuntuforums.org/showthread.php?t=80492")[/QUOTE]

I actually tried that before posting, and the problems still occurred. Additionally the errors occur using all engines.

---

### Post by nekr0z on 2006-04-07
Same for me here. Installed a new Audigy SE today and faced the same problem: on playing music the system freezes completely from time to time. Amarok freezes seldom, mpg123 more often, but they both do. The funniest thing is: when I play video with xine, everything is OK, but if I use xine engine in amarok, freezing occures.

Used to have some built-in Cirrus Logic sound before, with no problems (but terrible sound itself) at all. The issue only appeared on Audigy SE installation.

---

### Post by nekr0z on 2006-04-07
Well, now it freezes not so often: I switched off the built-in sound in BIOS, then booted up again. Pity they can't be used simultaneously, but it is anyway better than nothing.

But things could get even better if it didn't freeze at all!

---

