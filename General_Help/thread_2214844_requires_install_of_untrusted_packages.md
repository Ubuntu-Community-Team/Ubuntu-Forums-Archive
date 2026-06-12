---
title: "requires install of untrusted packages"
date: 2014-04-03
forum: General Help
---

### Post by roadyjr on 2014-04-03
[ATTACH=CONFIG]251681[/ATTACH]this is what i get and i cant update anything at all


PLEASE HELP MEEEE

---

### Post by grahammechanical on 2014-04-03
What did the "details" report? Have you installed any software through a Personal Package Archive (PPA)? Now, if you are using 12.04 you go into Software Sources and disable the PPA. If you are using 13.10 you go into Software and Updates and disable the PPA. What software are you trying to install? Where did not get it from? I am guessing that you have the option to either continue to install the software or that you cancel the installation of the software.

When we install software available in the Ubuntu Software Centre we get software from trusted sources. But we still have the freedom to download software from the Internet. If we do that then the installer warns us about the untrusted nature of the source of the software we are installing. We take responsibility for what we are doing.

Regards.

---

### Post by roadyjr on 2014-04-03
Yes I am using Ubuntu software center when I get this message and I don't know why I am getting this

---

### Post by XBNCPRk on 2014-04-03
If you click 'Details' on that error message, it will tell you which update has an issue.

---

### Post by Frogs Hair on 2014-04-03
Try the following from the terminal .```
 sudo apt-get update && sudo apt-get upgrade
```

---

