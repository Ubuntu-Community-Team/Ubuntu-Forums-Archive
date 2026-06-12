---
title: "Artefacts, screen flips"
date: 2013-03-19
forum: General Help
---

### Post by SPARTAN-118 on 2013-03-19
Hi all, been a while since I posted on these forums.

I've been using Ubuntu 12.10 with the default Unity config (tried Cinnamon but preferred it pre-config'd like in Mint).

I've noticed for a while now that at random times during the use of my computer, artefacts will appear all throughout the screen. They are usually either white boxes or the image itself becomes pixellated somewhat. I don't know if it's because of Unity or Compiz or the fglrx drivers or what. In addition to the artefacts, the entire screen flips upside down at random moments, usually while I'm browsing the Internet. In both situations, everything will go back to normal as I move the mouse around. In the case of the screen flip, I just had one, and was browsing a forum post in Google Chrome. At first, only a .gif signature image was right-side-up. Then, as I moved the mouse, the Chrome window fixed itself, and finally, I moved the cursor (which, by the way, does *not *get flipped) to the Unity Launcher. After that the entire screen was back to normal.

Anyone have any ideas? Oh, and though the Catalyst Control Centre is installed and I've changed some settings (including V-sync to Always On for a Tear-free desktop), Details in System Settings still says the VESA driver is being used. Is that a bug?

**Oh-hoh! **The screen flipped itself twice while I was typing this! Here's a screenshot of one of the instances. Note that after pressing Print Screen on my keyboard, the text input box flipped upright. Before I pressed it, it too was flipped.

---

### Post by ewangr on 2013-03-19
Any idea what graphics card you have? I have been trying to track down a similar issue where my Ubuntu installs but the display is "corrupted". I have an nVidia card and tried to install the nvidia specific drivers but that would cause the system to no longer recognize my monitor as a regular monitor (claims it's a laptop), gives me a clean display, but one that has massive black bars on both sides of the screen and no DASH. I am gathering from the threads I have already read that this may be particular to nVidia cards, but other threads seem to claim it's an issue with the x.org in 12.10. If it weren't that I spent a couple days setting up a 12TB RAID array and copying files to it, I might try and "backgrade" to 12.04, but at this point I'd rather deal with a funky screen than possibly have to redo that massive transfer.

FWIW...

---

### Post by SPARTAN-118 on 2013-03-19
You may have noticed the "fglrx" and "Catalyst Control Centre" in my first post. That means I have an AMD graphics card. :P
The ASUS HD 7770 (1 GB), to be exact.

I'm inclined to believe it's because of X, as well. That's why I'm actually looking forward to Mir, the Ubuntu-specific display manager. Some hate that they're abandoning X, but I say, if it helps solve my problems, go for it!

---

