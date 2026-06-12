---
title: "ipv6"
date: 2006-10-16
forum: General Help
---

### Post by xptweakerntn on 2006-10-16
i need to globally disable ipv6, how can i do that?

---

### Post by bollix47 on 2006-10-16
Have a look [here.]("http://www.ubuntuforums.org/showpost.php?p=932249&postcount=3")

---

### Post by bettlebrox on 2006-10-16
U can do the following:

Edit 

[INDENT]/etc/modprobe.d/blacklist[/INDENT]

And add the following lines to the bottom:

[INDENT]# blacklist the ipv6 module:
blacklist ipv6[/INDENT]

---

