---
title: "Help Me!!Not getting any Display!"
date: 2007-12-09
forum: General Help
---

### Post by mayur416 on 2007-12-09
I just completed installing Ubuntu 7.10 on my cousins system. The Installation was perfect and swift without any errors. After installatio when i tried to boot from the hard disk . there was no display:(:. I m not understanding what to do:confused:. Plz let me know what should i do...

---

### Post by overdrank on 2007-12-09
> **mayur416 said:**
> I just completed installing Ubuntu 7.10 on my cousins system. The Installation was perfect and swift without any errors. After installatio when i tried to boot from the hard disk . there was no display:(:. I m not understanding what to do:confused:. Plz let me know what should i do...

Hi what is the model of the graphics card? You can try and  when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command startx or to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by mali2297 on 2007-12-09
Try these tips:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

What kind of graphics card is it?

---

