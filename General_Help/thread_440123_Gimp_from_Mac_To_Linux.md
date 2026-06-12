---
title: "Gimp from Mac To Linux"
date: 2007-05-11
forum: General Help
---

### Post by efflux on 2007-05-11
Can anyone tell me if there is a way to transfer Gimp preferences from a Mac to Linux, specifically my tab arrangements? I know there is a file called gimprc but moving this doesn't seem to work. Thanks.

---

### Post by ArieT on 2007-05-11
I don't know anythink about mac but in Linux there is a map called $HOME/.gimp which contains all the settings (i think). This map also contains the gimprc file you've found. Perhaps you should copy the entire map.

---

### Post by efflux on 2007-05-11
Thanks for the reply. On the Mac I have similar files inside the Gimp.app. In etc/gimp/2.0 I can find a gimprc file. The only one I can find on my Mac. I've looked at the other files here and I don't see any info inside about any preferences. On my Mac this gimprc file contains what seems to be most basic preference settings but no info about how I have my tabs arranged so I need to find how Gimp Mac is saving my layout or how it saves this layout in Linux for that matter.

Not that it's a major problem to simply manually set Gimp up on Linux to be the same but I would like to know if it's possible to transfer these settings. For example I just installed Ubuntu 7.04 from scratch so lost my Gimp tab arrangement.

---

### Post by efflux on 2007-05-11
OK, forget the last message. I forget that the .gimp folder is hidden as it is on the Mac. The other gmprc will be a default. There is another gimprc in .gimp on my Mac.

---

### Post by efflux on 2007-05-11
OK here is the solution for anyone wanting to transfer their Gimp session layout which includes their tab arrangements. You need to transfer the file named sessionrc in home/.gimp-2.2. This holds your tabs layout.

---

