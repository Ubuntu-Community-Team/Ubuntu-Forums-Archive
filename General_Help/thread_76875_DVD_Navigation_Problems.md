---
title: "DVD Navigation Problems"
date: 2005-10-15
forum: General Help
---

### Post by randomc0de on 2005-10-15
So backstory, I was able to get DVD playback to work in Hoary and play some of the same DVD folders I'm now trying to play in Breezy. I've installed any package related to playing DVD's, and all the media players you could want. None work.

What happens is this - I'll open up a .vob file, and depending on the file, it may crash the player, it may play a speed-up version of the video, or it may actually play a slice of the whole movie.

So I'm fairly sure the problem is with the navigation and menus. I don't know why, but the media players just can't navigate the DVD. So has anyone else had this problem or knows what's going on?

What I've installed:
libdvdcss2
libdvdnav4
totem-xine
gxine
vlc and all the plugins
mplayer and mplayer-plugins
libdvd*
*dvd*

Thanks for any help.

---

### Post by avliet on 2005-10-16
Yup, definitely having issues with this - not happy.  I've tried using totem + totem-xine as well as gxine - nada.  gxine plays the disclaimers, federal warnings, etc. - then I get a pop-up box:
"xine engine error message:"
"Read error from: Error reading NAV packet."  

I have noticed that the federal messages, etc are played with libmpg2 - if the rest of the DVD is in mpg4, maybe there's an issue transfering to that new codec.  Still checking things out, but if anyone has any ideas...

---

### Post by randomc0de on 2005-10-16
What architecture are you using? Mine's AMD64. I got it working on Hoary i386 and I can't tell if the 64-bit part breaks it or if Breezy breaks it.

---

### Post by randomc0de on 2005-10-17
Anyone have new info on this or share the same problem?

---

