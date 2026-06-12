---
title: "how to install src.rpm file?"
date: 2008-06-23
forum: General Help
---

### Post by charbo on 2008-06-23
Hello,

I need to install the driver software found [here]("http://www.silabs.com/tgwWebApp/public/web_content/products/Microcontrollers/USB/en/mcu_vcp.htm") to the work machine.  

Apparently, they only provide the src.rpm file for linux platform.

How do I install a src.rpm file?
Can alien convert the src.rpm straight to binary deb file?
Is it best to install rpm, and build the binary rpm and then convert it to .deb?
Any better way of installing it?

Thank you for your consideration in advance!
Sadanori

---

### Post by Vivaldi Gloria on 2008-06-23
> **charbo said:**
> How do I install a src.rpm file?
Can alien convert the src.rpm straight to binary deb file?



```
sudo alien file.rpm
```

will create a deb file for you. Then double-click the deb file to install.

---

### Post by spiderbatdad on 2008-06-23
I believe the software you require is in synaptic package manager: "minicom."

---

### Post by charbo on 2008-06-24
I ran 
alien -k xxx.src.rpm
and it successfully created the xxx.deb package.

Thank you for your help!

---

