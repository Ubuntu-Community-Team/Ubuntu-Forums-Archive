---
title: "How to change scroll speed, there is no option"
date: 2019-12-21
forum: General Help
---

### Post by axima on 2019-12-21
Using ubuntu 18.04 in a parallels virtual machine on my MacBook Pro

The 2 finger scrolling is too fast, there is no setting to change it in the settings. I tried some terminal commands I found online but it makes no difference even if I set the number to 10. How can I slow down my scrolling speed?

[IMG]https://i.imgur.com/Zg2peZX.png[/IMG]
[IMG]https://i.imgur.com/8mb8PI4.png[/IMG]

---

### Post by Holger_Gehrke on 2019-12-21
Thanks to a wonder of virtualization performed by Parallels Ubuntu sees your touchpad as a generic clone of a MS Intellimouse Explorer connected through a PS/2 port. Obviously such a mouse has no parameters for two finger scrolling. You first need to make Parallels give Ubuntu a truer view of what is connected, then various parameters will become available for tuning. Or perhaps Parallels has some parameter for tuning that virtual mouse.

And please, when posting images in this forum use the 'Attachments' button in the advanced mode of the editor. This will produce thumbnails that can be enlarged instead of full-size images. Some of us are on slow or metered connections.
Also: text from a terminal can and should be cut and pasted (optimally in a code-block) instead of posted as a screenshot.

Holger

---

### Post by axima on 2019-12-21
> **Holger_Gehrke said:**
> Thanks to a wonder of virtualization performed by Parallels Ubuntu sees your touchpad as a generic clone of a MS Intellimouse Explorer connected through a PS/2 port. Obviously such a mouse has no parameters for two finger scrolling. [B]You first need to make Parallels give Ubuntu a truer view of what is connected, then various parameters will become available for tuning. Or perhaps Parallels has some parameter for tuning that virtual mouse.
[/B]
And please, when posting images in this forum use the 'Attachments' button in the advanced mode of the editor. This will produce thumbnails that can be enlarged instead of full-size images. Some of us are on slow or metered connections.
Also: text from a terminal can and should be cut and pasted (optimally in a code-block) instead of posted as a screenshot.

Holger

Ok, I see, how do I do that?

I'm using the touchpad on a 2014 15" MacBook Pro

TIA

---

