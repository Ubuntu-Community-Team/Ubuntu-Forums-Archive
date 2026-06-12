---
title: "ERROR si_upload_sw_state failed whenever I resume after suspend mode"
date: 2015-08-01
forum: General Help
---

### Post by Kabir_Gandhiok on 2015-08-01
Hi,

I'm new here, installed Ubuntu 14.04 LTS on Leveno G50 laptop. Partitioned with Windows 8.1. Today when I resumed my laptop from suspend mode, I got stuck on the black screen with this error message - ERROR: si_upload_sw_state failed. 

My machine would not go past the black screen, I had to keep the power on button pressed for a force shutdown and then start it back it. This error does not show up during restart or power up, only when I resume from suspend mode. Even when I manually suspend and then resume it back up I get this error. 

Tried looking if anyone else has had this problem, for a possible fix, but couldn't find anything.

Glad if someone could help me out here, thanks!
K

---

### Post by Kabir_Gandhiok on 2015-08-01
I've still not found a fix, but I feel this has something to do with the AMD X.org driver, which is selected by default. I feel this is so, because after posting this thread I tried switching to the fglrx driver and found the suspend problem was gone, later on I tried switching to fglrx-updates and the suspend problem still remained fixed but both the fglrx options gave minor, yet annoying problems, scrolling on firefox, ubuntu software centre and everywhere else with a long list to scroll through, was rough and broken, not smooth at all. So I switched back to X.org, which by the way, works really well, it's just this suspend problem. Anyway when I switched back to X.org and restarted my laptop, then after the grub menu I was welcomed by a black screen which listed a set of option on a white window saying my graphics are low and I need to fix it. I couldn't select any options because the keyboard was very unresponsive. 

I just went back to windows, deleted the Ubuntu partition, converted it to NTFS new volume and reinstalled Ubuntu 14.04 again on another partition, with more storage space this time (Lol). When the installation completed, I again saw X.org selected by default, so I suspended the laptop and got the same issue on resume. 

I don't want to use fglrx, I didn't like the experience I got from it, so I've just changed the Suspend options to Do Nothing from the Power settings. If anyone knows a fix for this, it would be very helpful, thanks!

---

### Post by Kabir_Gandhiok on 2015-08-03
No one knows how to fix this yet?

---

### Post by Vladlenin5000 on 2015-08-03
There isn't a fix. Or, better yet, the "fix" is exactly what you already tried. Those minor issues can *probably* be fixed as well but I'm far from an AMD expert. I suggest you try again the proprietary drivers, then post here your full configuration, namely the graphics card/chip, so others can help you troubleshooting.

---

