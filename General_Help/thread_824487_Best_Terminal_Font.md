---
title: "Best Terminal Font?"
date: 2008-06-10
forum: General Help
---

### Post by trappy on 2008-06-10
At the moment I am using Deja Vu Mono for my urxvt terminals, but it really ain't that nice. What can you recommend that's both nice looking and nice to the eyes?

---

### Post by kerry_s on 2008-06-10
that is pretty much the best truetype font. i use 9x15 for mine.

---

### Post by hugmenot on 2008-06-22
Are Xft fonts in your urxvt also running with wider character spacing than they should?

---

### Post by kerry_s on 2008-06-22
> **hugmenot said:**
> Are Xft fonts in your urxvt also running with wider character spacing than they should?

???
he's currently using a monospace font, mono fonts are evenly spaced, as are fixed fonts.
i use a fixed font(9x15) cause using truetype in a terminal is just a waste of resources to me, but then again i'm trying not to use truetype. :)
i prefer the faster, less resource bitmap fonts(aka: xfonts).

---

### Post by x1a4 on 2008-06-22
I vote size 14 dec terminal.  Add this to ~/.Xdefaults
```

urxvt*font:        -dec-terminal-medium-r-normal--14-140-75-75-c-80-iso8859-*
urxvt*boldFont:    -dec-terminal-bold-r-normal--14-140-75-75-c-80-iso8859-*

```
then execute ```
xrdb -merge ~/.Xdefaults
```

---

### Post by trappy on 2008-06-23
Damn, thanks for the try's, but STILL haven't found what I'm looking for. :(
Though, I don't really know what I am looking for. I just want a nice looking font that's nice to the eyes. :(

---

### Post by kerry_s on 2008-06-23
> **trappy said:**
> Damn, thanks for the try's, but STILL haven't found what I'm looking for. :(
Though, I don't really know what I am looking for. I just want a nice looking font that's nice to the eyes. :(

only you can decide, there are many fonts to choose from, just try them, you'll get the best look with fixed and mono type fonts.

my .Xdefaults, i don't use ttf, prefer the sharp look:

```
!! you need to run> xrdb -merge ~/.Xdefaults 

!*customization: -color
*Font: 9x15 
*fontSet: 9x15
*faceName: helvetica
*faceSize: 12
*saveLines: 10000
*scrollBar: false
*font: 9x15
*reverseVideo: true
*enableBackups: false

```

---

### Post by hugmenot on 2008-06-23
> **kerry_s said:**
> ???
he's currently using a monospace font, mono fonts are evenly spaced, as are fixed fonts.
i use a fixed font(9x15) cause using truetype in a terminal is just a waste of resources to me, but then again i'm trying not to use truetype. :)
i prefer the faster, less resource bitmap fonts(aka: xfonts).

I mean evenly spaced too wide:

```
urxvt -fn "xft:DejaVu Mono 9"
```

---

### Post by kerry_s on 2008-06-23
> **hugmenot said:**
> I mean evenly spaced too wide:

```
urxvt -fn "xft:DejaVu Mono 9"
```

ouch, my eye's. thanks for the screenshoot, i didn't realize truetype fonts have gotten so bad.
i use rxvt, so no ttf here.

---

### Post by x1a4 on 2008-06-23
There's a very nice tool called xfontsel, which allows you to preview and put together font aliases which you can use for rxvt.  I don't remember if it's installed by default or if you have to install it first, so you'll have to check.

---

### Post by trappy on 2008-06-23
> **x1a4 said:**
> There's a very nice tool called xfontsel, which allows you to preview and put together font aliases which you can use for rxvt.  I don't remember if it's installed by default or if you have to install it first, so you'll have to check.

Thanks, quite useful. It's installed by default. :)

---

### Post by rjmdomingo2003 on 2008-06-23
Try Terminus or Glisp (from the artwiz pack).

---

### Post by hugmenot on 2008-06-23
> **kerry_s said:**
> ouch, my eye's. thanks for the screenshoot, i didn't realize truetype fonts have gotten so bad.
i use rxvt, so no ttf here.

The font is good, urxvt is badly spacing the characters. I for one can&#8217;t stand pixel fonts and prefer good subpixel antialias.
You&#8217;re right that Xft is a lot slower, but I /need/ large fonts on my high resolution screen and pixel fonts fail at large sizes, they are simply to thin and pixelated.

Anyhow I&#8217;ve compiled a vte demo terminal app without any useless features. It is almost as fast as urxvt in Xft mode but supports more Unicode chars.

---

