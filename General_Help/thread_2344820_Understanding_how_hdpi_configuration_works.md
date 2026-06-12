---
title: "Understanding how hdpi configuration works"
date: 2016-11-28
forum: General Help
---

### Post by nachog on 2016-11-28
Hello

My display has 210 dpi. When I installed Ubuntu, I had to scale x2 everything and there is no problem with how things look. 

Nonetheless, when I run **xdpyinfo | grep dots **in the Terminal I get:** resolution:    96x96 dots per inch**, which I think is strange, since my dpi is 210. Does this means that I am not using my display at its full potential? Can someone help me understand why Xorg tells me my dpi is 96?

---

### Post by mcduck on 2016-11-28
try running "xrandr --dpi 210", and then disabling the scaling. Does that work?

Sadly it looks like Linux desktops have done same thing Windows has being doing all the time, and removed the DPI & subpixel arrangement settings and instead just decided to assume "standard" 96DPI for everyone and then give some basic UI scaling options. This used to be an option you could configure in font settings in Gnome2,but Gnome3 got rid of it.. (It *might* still be available through dconf, but if I remember right even that's not the case any more.)

Basically you *are* using all the pixels on your screen, but since the scaling won't make it match *exactly* with the pixels on the display panel, it's not going to look as crisp as it could be. Of course with high enough DPI on the display the difference becomes too small to notice, but being able to set the correct value easily would still be preferable.

Also, this could help: [http://askubuntu.com/questions/197828/how-to-find-and-change-the-screen-dpi]("http://askubuntu.com/questions/197828/how-to-find-and-change-the-screen-dpi")

---

### Post by nachog on 2016-11-28
Thank you for answering.

No, if I disable the scaling even after xrandr --dpi 210 everything looks tiny.

I wonder then what's the point of having a hidpi display if my os will just stretch everything to make it bigger.

---

