---
title: "Frozen Mouse and Touchpad after turning on screen sharing on my Smart TV"
date: 2023-02-19
forum: General Help
---

### Post by bobnutfield on 2023-02-19
Hello

I have screwed something up and my efforts to correct it have fallen short.  I am running 22.04 on a Dell Latitude i5.  I wanted to cast my screen to the TV (which I do all the time on a Mac.)  It only let me share media files and did not work.  This was over bluetooth (I believe and not the wifi).  Once I disconnected my mouse and touchpad do not work and I cannot get back to settings to reverse what I did (in the sharing portion of settings.)  I can open open a terminal from the keyboard, but I have no clue how to turn off what I did from the terminal.

Does anyone have any idea how to get my mouse and keyboard working again?

Any help is appreciated.

Bob

---

### Post by bobnutfield on 2023-02-19
Thanks for looking.  I was able to find the solution.  Running dconf reset -f / from the terminal solved it.  I had done very little tweaking so a full reset was not a problem.

Thanks

Bob

---

