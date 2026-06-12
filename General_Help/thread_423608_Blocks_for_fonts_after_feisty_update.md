---
title: "Blocks for fonts after feisty update"
date: 2007-04-26
forum: General Help
---

### Post by Pox on 2007-04-26
Well I did the Edgy -> Feisty update yesterday, all seemed to go smoothly.  Ran in to a couple of problems - 

Nvidia driver died, but I purged everything to do with it and reinstalled and all is fine now.

The second thing is that I'm having some troubles with pango font rendering.  On starting an app using Pango and utilising some specific fonts, I get this:

```
(gvim:5333): Pango-WARNING **: shape engine failure, expect ugly output. the offending font is 'Bitstream Vera Sans Mono Not-Rotated 8'
```

As far as I can tell, the only fonts effected are the Bitstream Vera family and the MSTTCorefonts.  However, this is a big problem, considering they are the fonts I use the most.

I've tried reinstalling pango, reinstalling my fonts, all to no avail - those fonts always break through pango.  Note though that they work perfect in OpenOffice.org 2.2, so it seems to be Pango-specific.

I've noticed a few other posts around here describing a similar problem, but no answers... anyone have any ideas whatsoever? TIA.

---

### Post by Pox on 2007-04-27
Note: I reinstalled Bitstream-Vera fonts and regenned font cache and all seems good :)

---

