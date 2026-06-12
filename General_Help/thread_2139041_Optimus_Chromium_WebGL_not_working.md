---
title: "Optimus Chromium WebGL not working"
date: 2013-04-25
forum: General Help
---

### Post by JaySeeJC on 2013-04-25
Have been having trouble with running WebGL apps in chrome/chromium for a while now. Problem has persisted for me through 12.04, 12.10, and now 13.04. My laptop hase nvidia optimus, but i don't see how this would prevent chromium from using intel's WebGL, unless it's not supported. Looking at about:gpu i get this at the top:

**Graphics Feature Status**


[LIST]
[*]Canvas: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Compositing: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]3D CSS: [COLOR=#FF0000]Unavailable. Hardware acceleration unavailable[/COLOR]
[*]CSS Animation: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]WebGL: [COLOR=#FF0000]Unavailable. Hardware acceleration unavailable[/COLOR]
[*]WebGL multisampling: [COLOR=#FF0000]Unavailable. Hardware acceleration unavailable[/COLOR]
[*]Flash 3D: [COLOR=#FF0000]Unavailable. Hardware acceleration unavailable[/COLOR]
[*]Flash Stage3D: [COLOR=#FF0000]Unavailable. Hardware acceleration unavailable[/COLOR]
[*]Texture Sharing: [COLOR=#FF0000]Unavailable. Hardware acceleration unavailable[/COLOR]
[*]Video Decode: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Video: [COLOR=#808000]Software only, hardware acceleration unavailable[/COLOR]
[*]Panel Fitting: [COLOR=#FF0000]Unavailable. Hardware acceleration disabled.[/COLOR]
[*]Force Compositing Mode: [COLOR=#FF0000]Unavailable. Hardware acceleration unavailable[/COLOR]
[/LIST]

Any help would be much appreciated. Thanks!

---

### Post by Gink on 2013-05-25
Try going to chrome://flags and enabling "Override Software Rendering List" then restarting Chromium. Hope it works for you!

---

