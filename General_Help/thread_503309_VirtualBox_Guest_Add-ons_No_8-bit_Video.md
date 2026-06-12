---
title: "VirtualBox Guest Add-ons: No 8-bit Video?"
date: 2007-07-17
forum: General Help
---

### Post by amklein on 2007-07-17
I recently installed windows xp using virtualbox on my ubuntu feisty box. By default, the highest resolution was 1024*768; and that just wasnt going to cut it. I installed guest additions but now you cannot select any lower than 16bit color quality! 

And this just wont cut it because I want to play some starcraft.

So, ive googled around and looked on this site and i have seen many reports of this problem but no solution. Am i missing something?

---

### Post by Twintop on 2007-07-17
When you load StarCraft, it will resize the window down to 640x480 (maybe 800x600, but I don't remember) anyway, and will not scale to take up the entire screen (yes, it is annoying). If all you're planning on using VirtualBox for is playing StarCraft, then it might be in your interest to uninstall the VirtualBox Tools completely (or the video adapter if at all possible) so you don't have the 8-bit error, since the resizing to more than 1024x768 resolution is a moot point and not possible for SC anyway.

If someone HAS gotten VMWare or VirtualBox to take up full screen in the SC sense, please let us know. I'd love to get it working but don't think it is possible.

---

