---
title: "mouse config keeps changing"
date: 2005-03-26
forum: General Help
---

### Post by jgeorgeson on 2005-03-26
I have a laptop with a synaptics touchpad. The default install left it fully configured. Both tap-to-click and vertical scrolling on the right edge both worked. To make it even better, hotplugging my usb mouse, both devices worked simultaneously. It was great. Ten the touchpad features tap/scroll stopped working. I didn't look at the original xorg.conf file, so I'm not sure if an update overwrote it and broke things, but I just added "CorePointer" and "AlwaysCore" to the the two InputDevice entries in the ServerLayout section, and all was well once again. Then it broke again. The ServerLayout section didn't change, but the InputDevice sections for the two mouse devices did. One had 'Option "CorePointer"' added and the other had 'Option "SendCoreEvents"' added. So I thought maybe those InputDevice options conflicted with the ServerLayout options  (the CorePointer was a different device in ServerLayout than it was in InputDevice). So I took the CorePointer/AlwaysCode out of the ServerLayout section. But that didn't work. So I added the options back in ServerLayout and took the CorePointer/SendCoreEvents options out of the InputDevice sections and it works again.

Which is the correct way? Which way does Ubuntu "try" to auto-configure it (so that I can try and get that way configured and not keep loosing my configuration)?

---

