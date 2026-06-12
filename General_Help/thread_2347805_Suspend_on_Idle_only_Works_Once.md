---
title: "Suspend on Idle only Works Once"
date: 2016-12-28
forum: General Help
---

### Post by alex.charchar on 2016-12-28
Hello!

I'm very new to the work of Linux, but have managed to get a media server setup and working almost perfectly. 

The only real problem I have is that I can't get the machine to suspend after it's been idle more than once. 

It does so once, but after I wake it up, the monitor, nor the machine, goes to sleep again at all, no matter how long its left on for. 

I'm running Lubuntu ([COLOR=#000000][FONT=Menlo]Ubuntu 16.10[/FONT][/COLOR]), on an old Dell Optiplex 755 Desktop. I've tried changing the settings in XFCE Power Manager as well as using dconf editor (editing: sleep-inactive-ac-timeout and sleep-inactive-ac-type). The XFCE options are being adhered to, but only the once. The changes I've made in dconf don't seem to have any effect, though I'm so far out of my depth in this that I might be missing something. I'm sure that it was previously falling into suspend when idle perfectly, but somewhere in the last few weeks (since I first set it up), it's no longer working.

I can suspend/wake up as much as I like using ```
systemctl suspend
```, then waking it up by hitting the power button.

If it makes any difference, my next step is to keep the machine awake whenever Plex is streaming using [this guide]("http://www.collindelker.com/wp/2016/10/plex-linux-prevent-sleep-take2/").

I would appreciate any advice or guidance in trying to get this figured out.

Thanks!

---

