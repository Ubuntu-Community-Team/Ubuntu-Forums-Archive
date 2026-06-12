---
title: "NHL.tv &amp; Flash Not Working"
date: 2016-12-27
forum: General Help
---

### Post by crizzo93 on 2016-12-27
Hey guys,

I recently switched to Ubuntu from Win10. I just installed flash using the terminal and it appears in ```
chrome:plugins
```. When I login to NHL.tv to watch a video, a white circle just loops over and over. I see the player controls load and the scrubber says 00:00.

Before I installed flash, I was seeing a box that said flash was not installed. So it must be installed and initializing, but no video appears to load. This is the same problem in Firefox as in Chromium. Got any suggestions? 

Thanks!

---

### Post by Dennis N on 2016-12-28
The newest flash player (version 24) no longer will support using protected flash content on Linux. Previously, we could install libhal1-flash to make it work, but adobe dropped support for this on Firefox starting with new flash player.

Check your flash player version at:

[http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/)

In Linux, Firefox with flash player 24 now supports some DRM but not for flash - see Preferences > Content and you can check the "Play DRM content" box. Click the "Learn More" link to the right of that to get full details about this.

Firefox with flash player 24 on Windows still works with flash DRM I believe, so that is a solution if you have it.

(I have the same problem - unable to log in on services I am entitled to through my cable TV.)

---

