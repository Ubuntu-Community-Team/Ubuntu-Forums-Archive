---
title: "[SOLVED] using screen for background apps"
date: 2007-01-16
forum: General Help
---

### Post by freeballer on 2007-01-16
I wanted a quick and dirty way to minimize apps after logging into my desktop using ssh and run them in background
I found "screen". Currently I use it by log into server using putty, screen [appname], then ctrl+A->D (minimize). I want to use irssi, elinks, mc, centericq, snownews

However I have a couple issues, midnight commander for one:
1) keys f1-f4 are not working 
2) either is mouse (not working at all, all programs)

Second I'm trying to make the title/name of the screen to be irssi
#1 "screen -t irssi"
#2         14991.pts-0.desktop     (Detached) <--- where's the name?

One issue that really ticks me off is with formatting or layout issues, I've tried switch -A/-a  but still seems to be formatted wrong (size for one) or getting a ghosting effect below an item. mostly effecting centericq and mc and sometimes make the program so useless I have to shut it down and restart.
Am I doing something wrong?  Is it possible to create a screen shell that looks and acts totally like my bash shell? If I messed up the command line options or not using right program for my use, let me know... I've tried using man screen and even googling issue but can't seem to find answer I'm looking for.

ALSO (while I'm already probably asking stupid questions)
Is there a way to make screen tabs to make all programs start at once, then use a keystroke like ctrl+alt+f1-f5 to scroll through them; f1 - irssi / f2 - centericq / f3 - elinks...... so instead of running seperate "screen irssi", "screen mc", etc... I can run one command and scroll through with hotkey(s)

---

### Post by freeballer on 2007-11-26
Posting a picture of said problem using putty to my htpc,
unfortunately this problem makes finch absolutely useless so I'd appreciate a response if someone has the answer.

Thanks

---

