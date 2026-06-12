---
title: "Autostart an app only after network is available?"
date: 2013-05-04
forum: General Help
---

### Post by MeMo_oMeM on 2013-05-04
Hi,

I am using desktop entries dropped in the ~/.config/autostart to open applications on login. One of these apps is the splashtop streamer. However this application loads before the wireless connection is established, therefore gives an error every time. Is there a way to load these applications after network, similar to the init scripts? If not, is there a way to artificially introduce a delay?

Thanks a lot inadvance!  

PS: I use 13.04

---

### Post by Frogs Hair on 2013-05-04
Here is a simple delay script , perhaps it could be modified to suit your needs .  You would have to add name and the path to the application , make it executable and add it to start up applications.  The sleep time can be changed . If you wait some one can help you further as I don't use scripts very often.      

```
#! /bin/bash
sleep 20

```

---

