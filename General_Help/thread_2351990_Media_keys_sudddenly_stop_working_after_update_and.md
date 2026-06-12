---
title: "Media keys sudddenly stop working after update and restart"
date: 2017-02-08
forum: General Help
---

### Post by lsutiger on 2017-02-08
I am currently running 14.04 64bit. My kernel version is 3.13.0-68-generic. My DE is gnome-flashback.
This system has been up and running smoothly for a couple of years. The media keys on my Logitech K530 have always worked.
That is until I had to do a restart due to an update. Now the media keys do not control the audio.
Through doing research to fix the problem, I came across [this thread]("http://askubuntu.com/questions/787257/media-keys-not-passing-after-upgrade-to-16-04") which states the issue may be with a rule file /lib/udev/rules.d/51-these-are-not-joysticks-rm.rules. This files does not exist on my system and I am on 14.04, so it is not that.
In the gnome keyboard settings, under the Shortcuts tab, the Sound and Media assignments are registering when I attempt to assign the keys. So the system is understanding the key press.
I also came across [this thread]("https://ubuntuforums.org/showthread.php?t=2217890") which states that the issue could be that an incorrect string is set in dconf key. The property for org.gnome.settings-daemon.plugins.media-upys volume- was  'AudioRaiseVolume', so I assigned it 'XF86AudioRaiseVolume'. No change.
I am at a loss on where to look next.
Help me troubleshoot this?

---

### Post by Autodave on 2017-02-08
This may sound dumb, but since no one else has responded yet........

I am assuming that you are referring to the laptop. If so, try powering it down, remove battery. Get a cup of coffee and enjoy drinking it. Reinsert battery and power back up.

I repair computers as a hobby, and I have fixed more than a few weird problems that way.

---

### Post by lsutiger on 2017-02-08
I appreciate the reply. It is the work computer.

---

### Post by lsutiger on 2017-02-09
I fixed the issue, in a clunky sort of way, but it works.
I have Compiz as the window manager, which I also have CCSM in order to manage Compiz.
There is a key binding option for commands. I turn that on and then I mapped the following commands to the Mute, Volume Up and Volume Down keys:
```
amixer -D pulse set Master toggle
amixer set Master 1+
amixer set Master 1-
```

---

