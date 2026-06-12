---
title: "installing ATI drivers with respositories?"
date: 2006-10-31
forum: General Help
---

### Post by cptjaben on 2006-10-31
HI, I was just wondering if there is a way that one can install the proprietary ATI drivers using the repositories and synaptic. Thanks

---

### Post by TigerCR1200 on 2006-10-31
In Synaptic search for fgrlx and install xorg-driver-fglrx.

However you will still have to edit the xorg.conf file and restart X or possibly reboot.

---

### Post by cptjaben on 2006-10-31
what will i need to edit in xorg.conf and how does one restart X in the terminal?

---

### Post by TigerCR1200 on 2006-10-31
You will need to tell xorg.conf to use the fglrx driver insead of ATI or RADEON in the Device section for your video card. 

To restart X you can press CTRL+ALT+Backspace. I am assuming you are already in X.

---

### Post by cptjaben on 2006-10-31
Thanks for the help everyone, it worked out well.

---

### Post by TigerCR1200 on 2006-10-31
Glad to hear it.

---

