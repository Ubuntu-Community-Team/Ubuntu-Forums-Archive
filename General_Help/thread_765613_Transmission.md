---
title: "Transmission"
date: 2008-04-24
forum: General Help
---

### Post by linux_newf on 2008-04-24
Earlier today i installed Hardy, it went well and it looks good.

I haven't gotten any of the updates yet, there still downloading.

Is this why Transmission doesn't seem to be working? What about flash in the FF browser?

Thanks

---

### Post by Archimedes0212 on 2009-01-26
Did you do a clean install or was it an upgrade.  I know that a lot of programs aren't available by default anymore (even in Intrepid). For example, I have to manually install VLC player whereas, when I first came to ubuntu, it was preinstalled.  That's just my guess though.

---

### Post by taurus on 2009-01-26
Transmission should be already on your system if you install hardy.  And regarding flash, java (Sun version), and codecs, you need to install them.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

