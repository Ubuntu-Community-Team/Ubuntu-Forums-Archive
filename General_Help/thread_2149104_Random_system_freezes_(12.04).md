---
title: "Random system freezes (12.04)"
date: 2013-05-27
forum: General Help
---

### Post by Subcomfreak on 2013-05-27
Hello again ubuntu forums, the place where I know I can always find an answer :D

Anyway, I have be experiencing a rather aggravating issue regarding my xubuntu 12.04 system. The issue is that at what appears to be at random the system completely freezes up. I try to jiggle the mouse, the touch pad, go to tty. Nothing gets it out of the freeze except a brute force shut down via the power button. Another symptom is that not only do the graphics freeze up, but also the audio (I use alsa mixer because it works best with my setup) sounds like a broken record over and over again until I reboot. 

So in essence the freeze is exactly like it sounds. Everything is locked in one position and there is no way out except via forced shut down.

I thought the freeze up might have been due to the 64 bit flash player... so using the firefox add-on "Flash-aid" I downgraded to the 32-bit drivers with no luck.

My current set-up is:
Xubuntu 12.04
Asus u47vc ([http://www.asus.com/Notebooks_Ultrabooks/U47VC/](http://www.asus.com/Notebooks_Ultrabooks/U47VC/))
using firefox as my web browser.
I'm currently not willing to upgrade to 13.04 because I like the long term support, and the system works perfectly except for this. 

Thank you all again. If you need any further information, simply ask.

---

### Post by Subcomfreak on 2013-05-28
Are there any specific log files that I need to provide for anyone to understand the nature of the problem?

---

### Post by 2F4U on 2013-05-30
Is there a pattern behind the lockups, for example such as always happens when browsing a site that uses flash in Firefox? Which graphics drivers are you using, proprietary nVidia or open source? The log file most relevant would probably /var/log/syslog. There is an application to view the file installed by default in Ubuntu Unity, but I am not sure about Xubuntu, but since its a text file you can open it with any editor.

---

### Post by Subcomfreak on 2013-05-30
Because it is optimus (*sigh*) I use bumblebee with open source drivers. I have tried switching between the two, with no change.

There does not seem to be a specific pattern. It locked up once before I ran anything. It locked up when only running a minecraft server. But most of the time it does lock up when view the web. I might try to completely remove flash, but I do need that to function. 

I'm not sure if a "Freeze" is caught on these dates. But when one does happen I will for sure post the log file, now that I know which one.

In order to post it I zipped it up, so you will have to unzip it.
[ATTACH]243281[/ATTACH]

---

