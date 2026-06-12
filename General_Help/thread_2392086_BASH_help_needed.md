---
title: "BASH help needed"
date: 2018-05-16
forum: General Help
---

### Post by ac7nj on 2018-05-16
"/home/randy/Enthought/Canopy_64bit/User/bin/activate: No such file or directory" I deleted Canopy but this message comes up every time I start BASH
how can I remove this Ubuntu 16.04 LTS

Thanks in advance
Randy AC7NJ

---

### Post by kazakore on 2018-05-16
Is it referenced somewhere in your bashrc file??

---

### Post by papibe on 2018-05-16
Hi ac7nj.

Could you open a terminal, run these commands, and paste back the results? (you can copy/paste the text with the mouse):
```
diff ~/.bashrc /etc/skel/.bashrc 

diff ~/.profile /etc/skel/.profile 
```
Regards.

---

