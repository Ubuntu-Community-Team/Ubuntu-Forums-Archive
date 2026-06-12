---
title: "Microphone Issue with Xubuntu"
date: 2015-02-26
forum: General Help
---

### Post by bryan44 on 2015-02-26
So I just installed Xubuntu on my Asus M11BB computer, and installed Skype the second I could..

I had called up a few friends on skype, only to be told there is an obnoxious buzzing/popcorn-like sound coming from my microphone.
I've been looking all over the internet for a fix, but to no avail what-so-ever.

I'm using Astro A40s (which worked fine for me on Windows) and really need some help with this issue because I uninstalled Windows entirely, idiot move I know, I just prefer Linux over Windows.


Thanks for your time,
Bryan

---

### Post by Thpn on 2015-02-28
If you're experiencing hum on an unbalanced line, the first thing I'd suspect is a bad connection. The crackling sound tends to confirm this. The A40 has a removable mic, so the connection there could be the problem. It also has a mute switch, which could be problematic. It could also be the plug, or the jack on your computer.

Try a different mic and see if you can eliminate the A40 as the cause of the issue.

---

### Post by bryan44 on 2015-02-28
Did that, same thing occurs with Turtle Beaches and a regular headset.

---

### Post by Thpn on 2015-03-03
Does the issue only occur when using Skype? Or, does this also happen when you record audio using something like Audacity?

---

### Post by bryan44 on 2015-03-03
> **Thpn said:**
> Does the issue only occur when using Skype? Or, does this also happen when you record audio using something like Audacity?

It occurs with everything related to recording my microphone. All ports on my computer seem to do this ONLY on Linux

---

### Post by Thpn on 2015-03-04
I'd suggest running Xubuntu 15.04 beta as a live distro to see if a kernel driver has been updated that fixes the problem. 

Or maybe try openSUSE "factory" to get an even more recent kernel. Also, SUSE is the main contributor to ALSA, so they might have implemented a solution that no one else has. 

Fedora "rawhide" has the most recent kernel, if you're really brave.

---

