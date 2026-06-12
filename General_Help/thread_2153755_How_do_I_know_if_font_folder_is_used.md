---
title: "How do I know if font folder is used?"
date: 2013-06-12
forum: General Help
---

### Post by bjorntj on 2013-06-12
If I run xset -q, then my truetype folder is not listed in Font Path...
Also inside /etc/fonts/fonts.conf the folder is not listed there either...

Can I then assume that my truetype fonts (inside /usr/share/fonts/truetype) is not used? And if so, where should I add this folder?


Regards,

BTJ

---

### Post by Cheesemill on 2013-06-12
What's the output of...
```
sudo fc-cache -fv
```

---

### Post by bjorntj on 2013-06-12
Well, there is my truetype fonts listed... So this is the command I can trust? :)

BTJ

---

### Post by Cheesemill on 2013-06-12
Yes. If a font directory is listed in the output of fc-cache then it is correctly installed and recognised by your system.

---

### Post by bjorntj on 2013-06-12
Ok... Thx... :)

BTJ

---

