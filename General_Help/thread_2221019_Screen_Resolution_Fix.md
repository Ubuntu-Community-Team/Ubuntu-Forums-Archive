---
title: "Screen Resolution Fix?"
date: 2014-04-30
forum: General Help
---

### Post by Niall_Carroll on 2014-04-30
Hi,

I'm having a few problem with screen resolutions on some ubuntu systesm. I have them button to TV's (3 32" TVs and 1 42" TV connected via HDMI) but anytime we set the resolution to anything more than 800x600 the system boots but the screens will not display anything, just blank screen?

First time using ubuntu, normally a windows or Mac man....is there such a thing as display drivers we need to install like on Windows?

Thanks for any help

Niall

---

### Post by kc1di on 2014-04-30
some cards need propriety drivers.  if you could go to a terminal and type ```
lspci | grep VGA
``` 
that will tell us the video card in use and we could advise as to the correct driver for you.

---

