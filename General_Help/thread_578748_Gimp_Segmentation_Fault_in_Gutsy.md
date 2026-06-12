---
title: "Gimp Segmentation Fault in Gutsy"
date: 2007-10-17
forum: General Help
---

### Post by abrichr on 2007-10-17
Yesterday I updated from Feisty to Gutsy, and noticed that several applications are now broken.

One of those is Gimp.  When I try to open an image, two out of three tries it will crash with the message:

```

$ gimp

(script-fu:7214): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
Segmentation fault (core dumped)

```

I'm using 2.4.0-rc3.  I've already tried reinstalling every gimp package in Synaptic.  Any suggestions?

---

### Post by Theosa on 2007-11-27
Try launching in terminal with:
G_SLICE=always-malloc gimp
You can also add G_SLICE=always-malloc to ~/.xinirc and start GIMP normally; but I'm not sure whether or not the second solution works with GDM.
Maybe adding a line to Session options or creating a little script and calling the script from Session options with "sh fullpathtoscript.sh" could work with GDM.

---

