---
title: "AMD binary driver 14.04"
date: 2014-04-22
forum: General Help
---

### Post by cranerja on 2014-04-22
I want to upgrade my machine to 14.04 but I can't seem to build the amd packages for 14.04 and I'd like to be on the most recent driver. Is there a way to do so? And if not, is there at eta on when amd will update the drivers for trusty?

---

### Post by cranerja on 2014-04-25
I've upgraded and I'm trying to create the packages but I still get an error. The log says Package build failed! and then gives the bad lines.

---

### Post by monkeybrain20122 on 2014-04-25
Which card is that?

---

### Post by cranerja on 2014-04-25
Oh! My apologies, this machine is Radeon HD 7870 but I'm building the packages for multiple computers.

---

### Post by mastablasta on 2014-04-26
that card should have suitable drivers in repositories. unless you plan to run development version?!

---

### Post by trag on 2014-04-26
get latest amd proprietary drivers using this,it worked like a charm for me  [http://sourceforge.net/projects/uaci/?source=directory](http://sourceforge.net/projects/uaci/?source=directory)
good luck
trag

---

### Post by cranerja on 2014-04-27
I run opengl games at high resolutions so I need dev versions. I ended up installing the dependencies from the project listed above and I could then package the drivers.

---

