---
title: "Almost all GUI applicaitons segfault"
date: 2008-03-17
forum: General Help
---

### Post by Oliver_U on 2008-03-17
Hi!

Backstory:
Nothing seemed to be wrong, I had recently done fiddling with my
hardware, but as my system has been running fine for a few days
since then I do not think it has anything to do with it.

The only thing I can suspect is causing the problem was a recent
update to VLC and related libraries that I got through the update
manager.

So what actually happened?

I was watching an episode of Penn & Teller using Totem, when I
accidentally invoked some compiz-command that made it a bit
transparent. I finished watching the episode, and as I didn't know
the command to undo the transparency, I thought I'd just restart
Totem (as I've done with other applications before).

I closed totem and, in nautilus, chose to open the next episode in
Movie Player (totem). No go. The cursor indicated activity by being
round for a while, and then stopped. I tried opening the same file
in VLC and got a slightly different result. VLC would show it's
graphical interface, and then crash.

Thinking a restart might help, I rebooted the computer. Bad idea.
Now when booting, only some programs would manage to start, while
others would start fine but crash whenever I tried to use them.

Basic overview of things:
ubuntu login screen works
gnome-panel doesn't work
gnome-do does start but crashes whenever I start searching.
the wallpaper image no longer loads, I get a black background instead
vlc doesn't work
rhythmbox doesn't work
totem doesn't work (logs at [http://owner.rnachoctb.org/totlog.txt](http://owner.rnachoctb.org/totlog.txt))
eog doesn't work
nautilus doesn't work
running and playing Diablo 2 in wine still works(!)
compiz still works flawlessly(!)
firefox works(!)
gnome-terminal still works
hotkey buttons for volume-changing still work
pidgin works

It seems most gui-applications will not work whenever they need
to load graphics? But that wouldn't explain how my windowing
environment works. Could it be that apps that use a specific toolkit
or library are the ones hanging?

The problem persists even when creating new users and logging in
under them, so it's not limited to just my user account.

No command line applications seem to be having any problems.

All applications that crash do so with a Segmentation Fault. :(
Everything works when I boot into windows, so the hardware is
not at fault. I've also run memtest86+ for 8h 24 minutes, covering
17 passes, without a single error.

The error log of gnome-do being started up and then used(crashed)
is available at [http://owner.rnachoctb.org/dolog.txt](http://owner.rnachoctb.org/dolog.txt)

I'd be extremely thankful for any help.

Regards,
Oliver

---

### Post by markharding557 on 2008-03-17
you say the problem started when you used a compiz command so i would try disabling compiz if you have'nt already

---

### Post by Oliver_U on 2008-03-17
Nope, doesn't work. As I mentioned, I tried creating a new user and logging in under it (new users do not have compiz enabled by default). I have also tried to run programs under my normal user without having compiz running, and that doesn't work either.

---

### Post by Oliver_U on 2008-03-17
SOLVED

Thanks to some guru friends on the internets, I managed to find what caused the error. The culprit was librsvg-2.18.2-2, which was fixed on upgrading to librsvg-2.22.2

Thanks anyways!

---

