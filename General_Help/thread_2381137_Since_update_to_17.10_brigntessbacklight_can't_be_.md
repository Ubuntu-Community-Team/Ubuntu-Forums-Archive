---
title: "Since update to 17.10 brigntess/backlight can't be changed (among other things)."
date: 2017-12-27
forum: General Help
---

### Post by paulakreuzer on 2017-12-27
I recently updated from 16.04 to 17.04, which rendered the device useless, because input was not possible (see here: [https://ubuntuforums.org/showthread.php?t=2380830](https://ubuntuforums.org/showthread.php?t=2380830)), then when I fixed that I upgraded right on to 17.10.

I didn't really use the device much between the two upgrades, so I don't know which upgrade might have caused the following issues.

Anyways after the upgrade I reenabled all disabled ppas, updated all software and rebooted, then I found that:


[LIST]
[*][COLOR=#a9a9a9]I can't change the screen brightness (backlight) anymore (keyboard shortcuts have no effect and in the system settings this option is completely missing)[/COLOR][COLOR=#a9a9a9] -[/COLOR][COLOR=#008000] fixed[/COLOR][COLOR=#a9a9a9] [COLOR=#a9a9a9]&#10004;&#65039;[/COLOR][/COLOR] - see EDIT 5 
[*][COLOR=#a9a9a9]Similarly I can't change the system volume & additionally it seems to be set to 0. Some programs that have their own audio-enhancement settings (like Kodi and 0ad) can play audio, but all others as well as the system are mute (system settings don't even display an output device).semi-fixed (&#10004;&#65039;) - see EDIT 2 -[/COLOR][COLOR=#008000] fixed[/COLOR][COLOR=#a9a9a9] [COLOR=#a9a9a9]&#10004;&#65039;[/COLOR][/COLOR] - see EDIT 4 
[*][COLOR=#a9a9a9]The setting for natural scrolling has no effect. - Workaround found - see EDIT 3 [COLOR=#a9a9a9] -[/COLOR][COLOR=#008000] fixed[/COLOR][COLOR=#a9a9a9] [COLOR=#a9a9a9]&#10004;&#65039;[/COLOR][/COLOR] [/COLOR]- see EDIT 4 
[*][COLOR=#a9a9a9]And last but not least some processes that didn't take any time before the upgrades now take ages, namely opening some apps (I was surprised before the upgrades that starting 0ad literally took less than a second, now it takes 20 seconds during which the computer doesn't seem to be busy) and opening menus (e.g. some system settings sub-menus, context menus in firefox, thunderbird and other apps as well as opening bookmark-folders from the bookmark toolbar - again these things take about 20 seconds during which the system seems to just wait, as though it interpreted my trackpad-clicks as "please do that in 20 seconds").[/COLOR] [COLOR=#008000]fixed[/COLOR] &#10004;&#65039; - see EDIT 1 
[/LIST]

So my uneducated guess would be that some files failed to download again during the upgrades. For audio and screen brightness I'd suspect drivers. Software & Updates -> Additional Drivers lists only 2 drivers: "NVIDIA Corp: GP106M" using NVIDIA binary driver - version 384.98 from nvidia-384 and "Unknown" using Processor microcode firmware for Intel CPUs from intel-microcode.

EDIT 1: I purged and re-installed pulseaudio, thinking this might fix the audio-issue. Strangely instead it fixed the speed issue. I can now start apps and open menus super fast again. Only 0ad doesn't open at all anymore, even after a purge and reinstall. The audio-issue is unaffected and pulseaudio still won't start because it can't connect to server.

EDIT 2: This guide ([https://askubuntu.com/questions/426648/how-to-reinstall-pulseaudio-ubuntu-12-04](https://askubuntu.com/questions/426648/how-to-reinstall-pulseaudio-ubuntu-12-04)) helped completely reinstalling and fixing pulseaudio. Now 0ad starts again and the audio issue is fixed.

EDIT 3: Actually the audio issue comes back after every reboot, because pulseaudio won't start automatically. I have to start if from the terminal after every reboot for audio to work properly.
Also I found a temporary fix for the scrolling issue here ([https://www.queryxchange.com/q/3_989400/natural-scroll-for-touchpad-in-lubuntu-17-10/](https://www.queryxchange.com/q/3_989400/natural-scroll-for-touchpad-in-lubuntu-17-10/)), but just as described there this also only works until the next reboot.
Does anybody have an idea how I can get these changes to stay permanently?

EDIT 4: I used "Startup Aplications" to automatically start pulseaudio and enable natural scrolling after reboot. So now only the missing brightness controls is left.

EDIT 5: Ok so now I finally fixed the last piece of the puzzle. Before the update I could decrease/increase the backlight with Fn + F8/F9. In Settings > Hardware > Keyboard I couldn't set up custom shortcuts for the same combination but I simply set *xbacklight -dec 10* and *xbacklight -inc 10 *to F8/F9 (without the Fn).

---

### Post by paulakreuzer on 2018-02-05
I managed to solve all the issues by myself over time. Topic can be closed.

---

