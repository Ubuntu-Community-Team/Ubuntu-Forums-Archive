---
title: "Unity freezes when switching from a tty"
date: 2016-07-22
forum: General Help
---

### Post by veddox on 2016-07-22
Hi everyone,

I recently installed Xenial on a used Thinkpad T420 I  bought. On the whole I'm quite pleased with it, but I have noticed one  thing that I find very annoying: occasionally, when switching from a tty  back to graphics mode, Ubuntu will freeze up. It seems be more likely  to happen if I have been working in the tty for some time. (I have only  been using this laptop and 16.04 for two weeks though, so I have not yet  discovered any other correlations.) A freeze usually lasts several  minutes, and I have to reboot afterwards (or during, if I don't feel  like waiting) in order to get Unity to run again.

The  problem occurred again last night during a fairly typical use scenario:  I was logged in on tty1,2,3 and 7 (tty7 being, as usual, the graphics  environment). Emacs was running in tty1. I don't think I had any other  programs currently running in any of the other ttys (though perhaps  Thunderbird or Nautilus on tty7). I have posted the relevant extract from my syslog [here]("https://paste.ubuntu.com/20443157/"). Unfortunately I cannot remember precisely when the freeze happened, but there is an error message by emacs that may be relevant at 00:25:35 in the log.

Previously I  used 14.04, I never encountered the problem there. My guess is that this  is some kind of a bug in Unity (or the X server?), but I don't really  know how to diagnose it properly or where I should file a bug report. It  is a pretty serious issue to me, as I do a fair amount of programming  in a tty (minimal distraction with optimum screen real estate usage).

I would appreciate some advice on how to proceed from here, I'm kinda stuck at the moment...

---

