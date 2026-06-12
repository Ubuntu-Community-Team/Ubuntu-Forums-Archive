---
title: "Laptop. Problem with brightness settings"
date: 2012-12-15
forum: General Help
---

### Post by sebastarzak on 2012-12-15
Hi every one. I have a laptop Toshiba staellite l-670 with core i3-380m. After installed all software update, I lost possibility changing brightness. I Have Ubuntu 12.04.1 LTS. 
Do you have any idea what I must do to get back possibility changing brightness ?

---

### Post by Pjotr123 on 2012-12-15
What's the output of:
```
lspci | grep -i vga
```

---

### Post by Rexilion on 2012-12-15
And please also the output of:

```
cat /var/log/Xorg.0.log
```

---

