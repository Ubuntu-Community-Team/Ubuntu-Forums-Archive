---
title: "Problem with module loading at boot."
date: 2017-03-24
forum: General Help
---

### Post by georgesgiralt on 2017-03-24
Hello !
I own a laptop with two video cards (optimus system). 
I would like to have the Intel card active at boot, so I set the switching system to use the Intel card. So far so good.
But the laptop activate the NVidia card at boot and sometimes forget to switch it off using too much of the battery. 
So I thought I could put :
```
 bbswitch load_state=0 
``` in /etc/modules.
Alas this is not working and I get the following in the logs : 
```
[FAILED] Failed to start Load Kernel Modules.
See 'systemctl status systemd-modules-load.service' for details.

```
 And of course, systemctl gives no clues as to what is wrong ... 
So all the help I can get will be greatly appreciated !

---

