---
title: "[SOLVED] Slow Session Startup; Why!?"
date: 2007-06-13
forum: General Help
---

### Post by TheThinker on 2007-06-13
Hello everyone who's willing to help me. Yesterday I installed three things on my computer along with their dependencies. They are Etherrape, Firestarter, and WineX from the WineHQ repositories (after deleting the Ubuntu WineX version using Synaptic). Things went along fine yesterday. I turned the PC off, then switched it back on to go online with Firestarter set to ON to test it out. Nothing seemed wrong at this point. According to Firestarter I got pinged a few times by outsiders and I assumed that they were successfully blocked. I shut it down and went to sleep.

Today, however, something is certainly wrong with Ubuntu. The system boots up fine in my opinion (although it could be faster), but when I log-in the GNOME desktop takes a long while to load up! What happens is that the screen blinks (which is usually normal), the orange-background appears and you see the Splash-screen. But the splash-screen doesn't have any loading-icons on it and it remains in place while my desktop icons and such are loading up. At this point you can notice that it takes a minute or two for all of the icons to load and for the wallpaper to replace the splash-screen. Very strange.

This is annoying for 3 reasons:
1) It seems as if some icons are slow to start up. For instance, when I press the power-button (to log-off, shut-down, or restart, etc) it takes around 1/2minute for its window to appear.
2) The File-manager seems slow as well. When I open Home, it takes roughly 1/2 minute to load up.
3) When I check the GNOME System Monitor to see if anything it soaking up memory and the CPU, everything but that program is "Sleeping" and the memory usage is at 100MB out of 248MB. This is normal, yet doesn't explain the slow-down in performance.

Attached is my auth.log from the Systems Log service. 

Sorry for the mess of info. I plan to get the system.log uploaded for all of you tomorrow, but with what you see here can anyone give me a solution? I recently turned on the "Terminal Multiplexor" service to no avail. 

Note: My compuer has dial-up internet access, so the programs I installed were done using an alternate computer and downloading the packages manually via flashdrive.

---

### Post by TheThinker on 2007-06-14
Alright! I recently did some research and have just fixed the problem. The problem was that I was messing around with the network settings in an attempt to establish a LAN connection with another computer. What I had done was delete one of the hosts files with the IP address 127.0.0.1 which had my Host-Name next to it. Doh! I re-created it and also added my host-name to the IP address 127.0.1.1 so that the alias reads as

localuser (my Host Name)

Not only is the desktop booting as fast as before, but now my file-system runs VERY fast! I'll include a link to a related article for anyone having similar problems tomorrow. see ya!

(In case anyone's confused, these network-settings are found in the System-->Network tab.)

---

