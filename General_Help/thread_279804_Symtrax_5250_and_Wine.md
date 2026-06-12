---
title: "Symtrax 5250 and Wine"
date: 2006-10-18
forum: General Help
---

### Post by josys36 on 2006-10-18
Folks,

I found a really good 5250 emulator that works under Wine. The product is Symtrax 5250. I have been using this product in Windows for a while, but never thought to try it under wine. The product does work, but I am having serious font issues. I can only get one font to be readable, and the others really wack out the screen. I love this 5250 product since it has a function to provide 5250 full screen. The one drawback is that I am having problems changing the colors for multiple sessions. 

Is anyone out there an expert on getting apps to work with Wine? I would write Symtrax support but they never provide support for this free product. Please let me know if more detail is required.

Thanks!

Jason

---

### Post by josys36 on 2006-10-18
The only font that seems to closely work is a font called plasmatic. I have never heard of it before, and I can't seem to find it on my system.

I think the trick is to find out where this product pulls in it's fonts.

Jason

---

### Post by josys36 on 2006-10-18
Well I made some progress. With a little searching I found a post that stated to make these registry changes.

HKEY_CURRENT_USER >> Software >> Wine >> X11 Driver (you'll need to create this key)

then add these two strings:

ClientSideWithCore
ClientSideWithRender

then set both of their values to "N"

I did and once I did there were a ton of new fonts available in the product. Now I just need to get currier new working. Currier New looks the best with this product in windows, but in Linux it is shrunk up to the top of the screen.

Jason

---

### Post by josys36 on 2007-08-13
Anyone have any other ideas?

Jason

---

