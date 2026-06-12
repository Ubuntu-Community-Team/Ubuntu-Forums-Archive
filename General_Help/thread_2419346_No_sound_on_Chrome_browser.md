---
title: "No sound on Chrome browser"
date: 2019-05-20
forum: General Help
---

### Post by satimis on 2019-05-20
Hi all,

Ubuntu 16.04

No sound on Chrome browser, Firefox having no problem with sound.

Please advise where I have to check for fixing this problem.

Thanks

Regards
satimis

---

### Post by #&amp;thj^% on 2019-05-20
have you installed pavucontrol>>> from the Terminal:
```

sudo apt install pavucontrol
```

To open pavucontrol from the Terminal:
```

pavucontrol
```

Select the "Playback" menu and make sure that you have it set to "Show Applications". Now, start playing something from Google Chrome. It will show up there, and it will show what output device is being used for Google Chrome. 

And before wiping out the entire Chrome configuration directory, try this: switch to another audio output device and then switch back to the original one. If you have only one audio device, connect an external one (like HDMI or USB audio) and then perform the above trick.

Update: The following seems to prevent the problem from reappearing in the future:

**>>>>Edit "/etc/pulse/default.pa"**, find the line that starts with "load-module module-stream-restore" and add "restore_device=false" at the end so that the line looks like this:

```
load-module module-stream-restore restore_device=false
```

And run" "killall pulseaudio"
Good Luck

---

### Post by satimis on 2019-05-20
> **1fallen said:**
> have you installed pavucontrol>>> from the Terminal:
```

sudo apt install pavucontrol
```

To open pavucontrol from the Terminal:
```

pavucontrol
```

Select the "Playback" menu and make sure that you have it set to "Show Applications". Now, start playing something from Google Chrome. It will show up there, and it will show what output device is being used for Google Chrome. 

And before wiping out the entire Chrome configuration directory, try this: switch to another audio output device and then switch back to the original one. If you have only one audio device, connect an external one (like HDMI or USB audio) and then perform the above trick.

Update: The following seems to prevent the problem from reappearing in the future:

**>>>>Edit "/etc/pulse/default.pa"**, find the line that starts with "load-module module-stream-restore" and add "restore_device=false" at the end so that the line looks like this:

```
load-module module-stream-restore restore_device=false
```

And run" "killall pulseaudio"
Good Luck
Hi,

Thanks for your advice.

Performed following steps

1) sudo apt install pavucontrol

2) start pavucontrol on Terminal
"Playback" --> "Show Applications"

3) On Terminal run;
$ sudo nano /etc/pulse/default.pa
Change;
load-module module-stream-restore
To:
load-module module-stream-restore restore_device=false

4) On Terminal
$ killall pulseaudio

No complaint

Still no sound.  I have to reboot PC then Chrome is now playing sound.

Regards
satimis

---

### Post by #&amp;thj^% on 2019-05-20
Are you running a Wayland session or a X session?

---

### Post by satimis on 2019-05-20
> **1fallen said:**
> Are you running a Wayland session or a X session?

X session

---

### Post by #&amp;thj^% on 2019-05-20
> **satimis said:**
> X session

You marked as SOLVED, is it?
EDIT:Right Then I'll assume it's a definite maybe. :p

---

