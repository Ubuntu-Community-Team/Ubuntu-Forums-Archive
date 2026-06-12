---
title: "Change from cyan text color in Fluxbuntu"
date: 2007-11-09
forum: General Help
---

### Post by orrie on 2007-11-09
I am using Fluxbuntu 7.10, just testing it and considering using in further on.
But I ran into a problem.

On Pidgin, in the address field in Firefox, in this message box and so on the font is cyan.
It's quite annoyning, and I have tried to change this in /usr/share/fluxbuntu/styles/ and no, it won't change.

I have been googling around for the last hour without finding out something smart..

Anybody know how to do this?

---

### Post by monthana on 2007-11-12
I have the same problem !
Anyone knows how to change this ?

---

### Post by toom87 on 2007-11-27
After much hunting I was able to determine it was related to the current theme specified in ~/.gtkrc-2.0 

The top include line was 
```
include "/usr/share/themes/Salsa/gtk-2.0/gtkrc"
```

Inside the theme gtkrc the variable responsible for the default text color was ntext_color and it was set to 000095959f9f which I guess must be Cyan, but when I changed it to 000 and restarted, the font was now black.

Rather than modify the Salsa theme though, I just used the Clearlooks theme instead which uses more natural fonts.

Now the top line of my ~/.gtkrc-2.0 reads
```
include "/usr/share/themes/Clearlooks/gtk-2.0/gtkrc"
```

---

### Post by orrie on 2007-12-14
Omg, perhaps I'll install Fluxbuntu again then :D

I really liked it, but the cyan stuff made me delete it.

---

