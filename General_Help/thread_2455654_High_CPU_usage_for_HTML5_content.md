---
title: "High CPU usage for HTML5 content"
date: 2020-12-24
forum: General Help
---

### Post by railgun744 on 2020-12-24
On a fresh 20.04 installation, Chromium/Brave/etc. do very well in term of CPU consumption until any kind of HTML5 content is loaded (easy to reproduce on Youtube), which suddenly makes the browser a lot more hungry.

Example of the setup on Brave:
[COLOR=#000000][FONT=sans-serif][/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif][h=3]Graphics Feature Status[/h]
[LIST]
[*]Canvas: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Compositing: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Multiple Raster Threads: [COLOR=#008000]Enabled[/COLOR]
[*]Out-of-process Rasterization: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]OpenGL: [COLOR=#008000]Enabled[/COLOR]
[*]Hardware Protected Video Decode: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Rasterization: [COLOR=#008000]Hardware accelerated on all pages[/COLOR]
[*]Skia Renderer: [COLOR=#008000]Enabled[/COLOR]
[*]Video Decode: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]Vulkan: [COLOR=#FF0000]Disabled[/COLOR]
[*]WebGL: [COLOR=#008000]Hardware accelerated[/COLOR]
[*]WebGL2: [COLOR=#008000]Hardware accelerated[/COLOR]
[/LIST]
[/FONT][/COLOR]
Any ideas about how to fix this?

---

### Post by CatKiller on 2020-12-24
That isn't because of HTML5, it's because you don't have hardware acceleration for the video codec being used: likely VP9. There's an extension to request H.264 instead.

---

### Post by railgun744 on 2020-12-24
> **CatKiller said:**
> That isn't because of HTML5, it's because you don't have hardware acceleration for the video codec being used: likely VP9. There's an extension to request H.264 instead.

Do you mean this one?
[https://chrome.google.com/webstore/detail/h264ify/aleakchihdccplidncghkekgioiakgal](https://chrome.google.com/webstore/detail/h264ify/aleakchihdccplidncghkekgioiakgal)

It seems to only work on youtube, though.

---

### Post by railgun744 on 2020-12-24
Apparently there is some problem that causes the browser to fall back on FFMpeg for playback audio and video.

---

