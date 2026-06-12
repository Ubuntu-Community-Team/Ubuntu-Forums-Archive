---
title: "Usplash For Edgy - Progress and text color"
date: 2006-11-16
forum: General Help
---

### Post by bleucanard on 2006-11-16
I have created a new multi resolution usplash using the usplash-dev package
and the example included in it but I think I stumbled on a usplash bug.

When using the custom drawing for the progress bar (using throbber_fore and throbber_back) everything works fine : my .so library is drawing ther progress using a png file, and everything is fine.

However when removing the drawing code and relying on the default usplash
behaviour, the colours of the progress bar are wrong. In that case, usplash is supposed to draw the progress as a standard rectangle, using 2 colours passed as an index into the png's palette.However the colours that
appears are not right: 0 to 0x20 maps to blue, 0x20 to 0x3f maps to green, etc.,.., and I haven't even got any of these in my png. In that they map to the same colours no matter what my palette is.

The png is a 255 color index, created in the gimp. It appears fine on
the screen. The text suffers from the same problem. I also noticed that in the default ubuntu usplash, if I remove quiet from grub options, the text appears in blue and clashes horribly with the rest (if I were a conspiracy theorist, I'd say that's why Edgy defaulted to quiet rather than verbose on startup, because they couldn't fix it in time for release......)

It looks to me as if usplash is not setting the palette properly (or it could be a bogl problem). 

Another thing I noticed when experimenting: if I create my own init function in the .c file for the .so library, and repeatedly call usplash_set_palette, the png does not appear properly anymore. The more I call set_palette, the darker it gets. After  3 or 4 calls, the screen just gets black; this may be indicative of a usplash or bogl problem ?



Pierre

---

### Post by ciscosurfer on 2006-11-16
That's interesting and I can confirm the blue-text-quiet 'bug' as well.  I think I'm going to look into this a bit further.

---

### Post by bleucanard on 2006-11-17
It's amazing what you find once you know what to look for :)
it looks like it's a bug :

[https://launchpad.net/distros/ubuntu/+source/usplash/+bug/64171](https://launchpad.net/distros/ubuntu/+source/usplash/+bug/64171)

I've tried to recompile usplash but I'm getting nowhere (0.4.33 from launchpad), it won't even initialise the screen. I guess I'll have to wait...

---

