---
title: "I disabled all plugins, but gedit is still slow"
date: 2013-12-30
forum: General Help
---

### Post by sha1sum on 2013-12-30
Gedit sometimes respons very slow (think 8 seconds), and it also slows down other programs.

This problem has been reported before, ( for example here: [http://ubuntuforums.org/showthread.php?t=938208](http://ubuntuforums.org/showthread.php?t=938208) ) and the solution that was given was to disable certain plugins, which seemed to work for others.

However... I disabled all plugins in gedit but that hasn't changed anything for me. What do I do now?

---

### Post by Dreamer Fithp Apprentice on 2013-12-30
That's a very old thread you linked to. I doubt it's the same bug, but it could certainly be similar. Did you try rebooting after you unistalled the presumed offending plugins? You might also try looking at some sort of system monitor when it does this to find out exactly what resource is in short supply and what is using it up. I use lxtask. You may have gnome-system-monitor. I'm not sure what comes with the default installation now. You can of course install any you want. Lxtask is graphical and doesn't hog too much RAM or CPU itself.  Or there are some that work in a terminal, like top. Gedit, even with a bunch of plugins, shouldn't be slow. You might try leafpad instead until you figure out what's wrong with gedit.

---

### Post by vasa1 on 2013-12-30
> **sha1sum said:**
> Gedit sometimes respons very slow (think 8 seconds), ...
Are you just opening gedit or are you opening a large file with gedit? There are reports of gedit having difficulties with large files.

---

### Post by sha1sum on 2013-12-31
No, the issues also occur while just starting gedit without any file.

> **Dreamer Fithp Apprentice said:**
> That's a very old thread you  linked to. I doubt it's the same bug, but it could certainly be similar.  Did you try rebooting after you unistalled the presumed offending  plugins? You might also try looking at some sort of system monitor when  it does this to find out exactly what resource is in short supply and  what is using it up. I checked system monitor and I see a spike  in CPU usage when opening gedit.

---

### Post by Dreamer Fithp Apprentice on 2014-01-02
Sounds like a bug to me. I just opened gedit and it was the absolute LAST in the lxtask list when ordered by cpu usage. You will gain much karma by filing a detailed bug report. You don't say what version of Ubuntu or gedit you're using. Perhaps there is an upgrade available? Or you could try some other editors. Pluma is the most like gedit. You can get it from the Mate repository. Directions at [http://mate-desktop.org](http://mate-desktop.org)

---

### Post by sha1sum on 2014-01-03
Thanks for your reply. I'm currently using 12.04 (precise) 32-bit and the GEdit Version 3.4.1 that comes with it by default. As long as I can't pinpoint the problem, I don't want to waste the developer's time with a vague bug report. If I know what causes the problem, I will definitely inform them. Again thanks for your reply.

---

### Post by Dreamer Fithp Apprentice on 2014-01-05
For whatever it's worth, Saucy 13.10 uses Gedit 3.8.3. In general I've had a much better experience with it than I did with Precise, which I continued to use on one system until pretty recently. But I don't recall any problems with gedit specifically. The most noticable improvements for me were in Pcmanfm and Thunar. The only thing I've noticed not working as well or better is Synaptic which crashes way too often now, requiring me to go to a tty and pkill it before anything in x will respond. My experience may not be typical as I use plain openbox for a DE, sans Desktop, sans panel, not any of the, ahem, canonical setups.

---

### Post by sha1sum on 2014-01-05
Thanks for your sharing your experiences. I think I'm also going to update to Saucy (or Trusty when it comes out) one of these days.

---

