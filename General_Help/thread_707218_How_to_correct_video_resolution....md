---
title: "How to correct video resolution...???"
date: 2008-02-25
forum: General Help
---

### Post by cyberazi on 2008-02-25
I think i screwed up my video resolution when i ran the Ubuntu update for my laptop ATI drivers...

BTW my laptop is using Ati x700M gfx 

so anyone knows how to recover from this???

---

### Post by Sam Lars on 2008-02-25
Try a
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by cyberazi on 2008-02-25
okay cool it works but now my resolution cannot go back to wide screen and the image is still squashed...

how to i install the driver from ATI website.. i tried the *.run but cannot leh

---

### Post by chalewa on 2008-02-25
there is a wiki on the ati website on how to manually install the fglrx driver.


assuming you are running gutsy

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)



and edit2: before you go and reinstall all that post ```
fglrxinfo
``` and your xorg.conf

---

