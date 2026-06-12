---
title: "Bluetooth headphones lags / delay"
date: 2017-11-24
forum: General Help
---

### Post by maor44 on 2017-11-24
[COLOR=#111111][FONT=Ubuntu]I have a problem with Bluetooth headphones. when I connect them I have a delay in youtube and other videos. also, there is a lot of little disconnected. these headphones work perfectly in windows. the problem is only in Ubuntu. I tried to download blueman and it’s still the same - not working.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I really love Ubuntu and want to work with it but, if I cant use these headphones, I will have to go back to windows.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]PLEASE HELP! Thanks.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]P.S ubuntu 16.04[/FONT][/COLOR]

---

### Post by Bryan76 on 2017-12-11
I am experiencing the same issue with 17.10. [https://ubuntuforums.org/showthread.php?t=2379063&highlight=youtube+bluetooth](https://ubuntuforums.org/showthread.php?t=2379063&highlight=youtube+bluetooth)

---

### Post by Yellow Pasque on 2017-12-11
Possibly relative: [https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Bluetooth_headset_replay_problems](https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Bluetooth_headset_replay_problems)

---

### Post by Bryan76 on 2018-01-05
> **Temüjin said:**
> Possibly relative: [https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Bluetooth_headset_replay_problems](https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Bluetooth_headset_replay_problems)

I commented out **load-module module-suspend-on-idle** in **/etc/pulse/default.pa** and that did not solve the problem.

I also verified that **module-suspend-on-idle **did not appear in any file under [B]~/.config/pulse/

[/B]No luck.  The delays are still there.
Any other thoughts?

---

### Post by kdavh on 2018-01-15
I'm struggling with the same issue (16.04 , Dell XPS 13). 

I do notice the breaks in sound which start the delay, each break increasing the delay.  The breaks happen when I'm too far from the bluetooth audio source, or I think sometimes when my wifi is weak so it's working hard, it interferes with the bluetooth.

It looks like this solved the wifi interference problem for one person: [https://ubuntuforums.org/showthread.php?t=2364633](https://ubuntuforums.org/showthread.php?t=2364633)
But it may not be easily reproducible on different hardware... so...

Anyway, the best way I've found so far to quickly reset the delay is to run `pactl suspend-sink 1 && pactl suspend-sink 0`(see here: [https://bugs.freedesktop.org/show_bug.cgi?id=58746](https://bugs.freedesktop.org/show_bug.cgi?id=58746)).  I'm sure there is some better way, but I haven't found it yet.

---

